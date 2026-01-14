# User Guide - Divi

## Table of Contents
1. [Create a New Case](#create-a-new-case)
2. [Load Configuration in Settings](#load-configuration-in-settings)
3. [JSON Configuration File](#json-configuration-file)
4. [Save and Submit Cases](#save-and-submit-cases)
5. [View Existing Cases](#view-existing-cases)
6. [Temporary Export (USB)](#temporary-export-usb)
7. [Application Settings](#application-settings)

---

## Create a New Case

### Accessing the Creation Form
1. On the home screen, tap the **"New case"** button (folder icon with a "+")
2. The case creation form opens

### Filling Out the Form

The form displays fields defined in your JSON configuration. Available fields may vary depending on your custom configuration.

**Possible Field Types:**

- **Text fields**: To enter text (one line or multiple lines)
- **Dropdown lists**: To select one or multiple options
- **Icon selection**: To choose an option via visual icons
- **Standard fields**: Gender, age, description, etc. (depending on your configuration)

**Photos**
- Tap the **"Take a photo"** button (camera icon)
- Take at least **5 photos if possible** for better documentation
- Each photo is automatically geolocated if location permission is granted
- Taken photos appear below the button

### Form Validation
Before you can save or submit a case, you must fill in:
- **At least one photo** (always required)
- **All fields marked as mandatory** in your JSON configuration

**Important note:** Required fields depend entirely on your JSON configuration. Fields with `"mandatory": true"` in your JSON file will be required. If a required field is missing, an alert message will indicate exactly which field needs to be completed.

---

## Load Configuration in Settings

### Accessing Configuration Settings
1. On the home screen, tap the **Settings** icon in the top right
2. Select the **"Configuration"** tab (Admin)

### Load a Custom Configuration

**Step 1: Prepare Your Configuration File**
- Your configuration must be a valid JSON file
- The file must be accessible via a URL (hosted on a web server)
- See the [JSON Configuration File](#json-configuration-file) section for details

**Step 2: Enter the URL**
1. In the **"Form Configuration"** field, enter the complete URL of your JSON file
   - Example: `https://example.com/config.json`
2. Tap the **"Load configuration"** button

**Step 3: Verify Loading**
- If loading succeeds, a confirmation message appears
- The configuration is immediately applied to new cases
- The URL is saved and displayed as "Current configuration"

**In Case of Error**
- An error message appears if:
  - The URL is invalid
  - The JSON file is malformed
  - The server is not accessible
- Check the URL and try again

---

## JSON Configuration File

### Basic Structure

The JSON configuration file must follow this structure:

```json
{
  "fields": [
    {
      "key": "field_name",
      "type": "field_type",
      "mandatory": true,
      "personalized": false,
      ...
    }
  ]
}
```

### Common Properties for All Fields

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `key` | string | Yes | Unique field identifier (used to store the value) |
| `type` | string | No* | Field type (see available types below) |
| `mandatory` | boolean | No | If `true`, the field is required (default: `false`) |
| `personalized` | boolean | No | If `false`, uses the app's standard fields (default: `false`) |
| `label` | object | No | Translated label: `{"fr": "Text", "en": "Text", "es": "Texto", "ar": "نص"}` |
| `placeholder` | object | No | Help text translated (same format as `label`) |
| `emptyText` | object | No | Text displayed when no value (same format as `label`) |
| `multiple` | boolean | No | If `true`, allows multiple selection (default: `false`) |
| `options` | array | No* | List of options for dropdown/icons (see examples) |

**Important notes:**
- *`type` is required for personalized fields (except for some standard fields like `description`)
- *`options` is required for `dropdown`, `simpledropdown`, and `icons` types (because these fields need a list of options to display)

### Available Field Types

#### 1. Text Field (`"type": "text"`)

For entering short text (one line).

**Example:**
```json
{
  "key": "field_name",
  "label": {
    "fr": "Field name",
    "en": "Field name",
    "es": "Nombre del campo",
    "ar": "اسم الحقل"
  },
  "type": "text",
  "mandatory": true,
  "personalized": false,
  "placeholder": {
    "fr": "Enter a value",
    "en": "Enter a value",
    "es": "Ingresar un valor",
    "ar": "أدخل قيمة"
  }
}
```

#### 2. Multiline Text Field (`"type": "textarea"`)

For entering long text (multiple lines).

**Example:**
```json
{
  "key": "comments",
  "label": {
    "fr": "Comments",
    "en": "Comments",
    "es": "Comentarios",
    "ar": "تعليقات"
  },
  "type": "textarea",
  "mandatory": false,
  "personalized": false,
  "placeholder": {
    "fr": "Add comments...",
    "en": "Add comments...",
    "es": "Agregar comentarios...",
    "ar": "أضف تعليقات..."
  }
}
```

#### 3. Dropdown (`"type": "dropdown"`)

For selecting **multiple options** from a list. Displays options in a dropdown list with support for multiple selection. Options contain only text (label + value), no icons.

**Required:** This type requires the `options` property with a list of options.

**Note:** This type is designed for multiple selection. For single selection, use `simpledropdown`.

**Example:**
```json
{
  "key": "category",
  "label": {
    "fr": "Category",
    "en": "Category",
    "es": "Categoría",
    "ar": "فئة"
  },
  "type": "dropdown",
  "mandatory": true,
  "personalized": false,
  "placeholder": {
    "fr": "Select a category",
    "en": "Select a category",
    "es": "Seleccionar una categoría",
    "ar": "اختر فئة"
  },
  "emptyText": {
    "fr": "No category",
    "en": "No category",
    "es": "Sin categoría",
    "ar": "لا توجد فئة"
  },
  "options": [
    {
      "label": {
        "fr": "Option 1",
        "en": "Option 1",
        "es": "Opción 1",
        "ar": "خيار 1"
      },
      "value": "option1"
    },
    {
      "label": {
        "fr": "Option 2",
        "en": "Option 2",
        "es": "Opción 2",
        "ar": "خيار 2"
      },
      "value": "option2"
    },
    {
      "label": {
        "fr": "Option 3",
        "en": "Option 3",
        "es": "Opción 3",
        "ar": "خيار 3"
      },
      "value": "option3"
    }
  ]
}
```

**Note on multiple selection:**
The `dropdown` type allows multiple selection by default. If you want single selection, use `simpledropdown` instead.

#### 4. Icon Selection (`"type": "icons"`)

For selecting **a single option** via visual icons. Single selection only.

**Example:**
```json
{
  "key": "type",
  "label": {
    "fr": "Type",
    "en": "Type",
    "es": "Tipo",
    "ar": "نوع"
  },
  "type": "icons",
  "mandatory": true,
  "personalized": false,
  "placeholder": {
    "fr": "Select a type",
    "en": "Select a type",
    "es": "Seleccionar un tipo",
    "ar": "اختر نوعًا"
  },
  "options": [
    {
      "label": {
        "fr": "Type 1",
        "en": "Type 1",
        "es": "Tipo 1",
        "ar": "نوع 1"
      },
      "value": "type1",
      "icon": "https://example.com/icons/type1.png"
    },
    {
      "label": {
        "fr": "Type 2",
        "en": "Type 2",
        "es": "Tipo 2",
        "ar": "نوع 2"
      },
      "value": "type2",
      "icon": "https://example.com/icons/type2.png"
    },
    {
      "label": {
        "fr": "Type 3",
        "en": "Type 3",
        "es": "Tipo 3",
        "ar": "نوع 3"
      },
      "value": "type3",
      "icon": "https://example.com/icons/type3.png"
    }
  ]
}
```

**Important Notes for Icons:**
- The icon URL must be publicly accessible
- Supported formats: PNG, JPG, JPEG
- Recommended size: 200x200 pixels minimum
- **Image format:** 1:1 aspect ratio (square format). If images do not meet this ratio, they will be resized, which may lead to stretching
- Icons are downloaded and cached when loading the configuration
- Each option in the `options` array can have an `icon` property with a direct URL to the image

#### 5. Simplified Dropdown (`"type": "simpledropdown"`)

For selecting **a single option** from a dropdown list. Single selection only, without icon support in options. Options can only contain text (label + value).

**Required:** This type requires the `options` property with a list of options (but without `icon` property in the options).

**Summary of differences:**
- **`icons`**: Single selection via visual icons (each option can have an icon)
- **`dropdown`**: Multiple selection in a dropdown list (text only, no icons)
- **`simpledropdown`**: Single selection in a dropdown list (text only, no icons)

**Example:**
```json
{
  "key": "status",
  "label": {
    "fr": "Status",
    "en": "Status",
    "es": "Estado",
    "ar": "الحالة"
  },
  "type": "simpledropdown",
  "mandatory": false,
  "options": [
    {
      "label": {
        "fr": "Option 1",
        "en": "Option 1",
        "es": "Opción 1",
        "ar": "خيار 1"
      },
      "value": "option1"
    },
    {
      "label": {
        "fr": "Option 2",
        "en": "Option 2",
        "es": "Opción 2",
        "ar": "خيار 2"
      },
      "value": "option2"
    },
    {
      "label": {
        "fr": "Option 3",
        "en": "Option 3",
        "es": "Opción 3",
        "ar": "خيار 3"
      },
      "value": "option3"
    }
  ]
}
```

### Special Predefined Fields

Some fields have special behaviors when using specific keys with `"personalized": false`:

#### Available Standard Fields

**`"key": "sex"`** - Gender/Sex
- With `"type": "icons"`: Displays standard icons (👩 Female, 👨 Male, ❓ Unknown)
- With `"type": "simpledropdown"`: Dropdown with standard options
- **Required by default** if `"mandatory": true"` is not specified (can be made optional with `"mandatory": false`)

**`"key": "age"`** - Age
- With `"type": "icons"`: Displays standard icons (👶 Child, 👤 Adult, 👴 Senior)
- With `"type": "text"`: Numeric text field to enter age
- **Required by default** if `"mandatory": true"` is not specified (can be made optional with `"mandatory": false`)

**`"key": "description"`** - Description
- Standard multiline text field
- No need to specify `type`, it is automatically `textarea`
- **Optional by default** (make it required with `"mandatory": true`)

**`"key": "types"`** - Case Types
- Used for case types (must have `options`)
- **Required by default** if `"mandatory": true"` is not specified (can be made optional with `"mandatory": false`)

**`"key": "tagID"`** - Tag Identifier
- Text field to enter a custom identifier
- **Optional by default**

**`"key": "ethnicity"`** - Ethnicity
- Standard text field
- **Optional by default**

**`"key": "injury"`** - Injury
- Text field to describe the cause of injury
- **Optional by default**

**Important note:** For all fields, you can control whether they are required or not with the `"mandatory"` property. Only **photos are always required**, regardless of configuration.

### Complete Configuration Example

```json
{
  "fields": [
    {
      "key": "types",
      "personalized": false,
      "mandatory": true,
      "options": [
        {
          "label": {
            "fr": "Type 1",
            "en": "Type 1",
            "es": "Tipo 1",
            "ar": "نوع 1"
          },
          "value": "type1"
        },
        {
          "label": {
            "fr": "Type 2",
            "en": "Type 2",
            "es": "Tipo 2",
            "ar": "نوع 2"
          },
          "value": "type2"
        },
        {
          "label": {
            "fr": "Type 3",
            "en": "Type 3",
            "es": "Tipo 3",
            "ar": "نوع 3"
          },
          "value": "type3"
        }
      ]
    },
    {
      "key": "sex",
      "type": "icons",
      "mandatory": true,
      "personalized": false
    },
    {
      "key": "age",
      "type": "icons",
      "mandatory": true,
      "personalized": false
    },
    {
      "key": "field_name",
      "label": {
        "fr": "Field name",
        "en": "Field name",
        "es": "Nombre del campo",
        "ar": "اسم الحقل"
      },
      "type": "text",
      "mandatory": true,
      "personalized": false,
      "placeholder": {
        "fr": "Enter a value",
        "en": "Enter a value",
        "es": "Ingresar un valor",
        "ar": "أدخل قيمة"
      }
    },
    {
      "key": "category",
      "label": {
        "fr": "Category",
        "en": "Category",
        "es": "Categoría",
        "ar": "فئة"
      },
      "type": "dropdown",
      "mandatory": false,
      "personalized": false,
      "options": [
        {
          "label": {
            "fr": "Option 1",
            "en": "Option 1",
            "es": "Opción 1",
            "ar": "خيار 1"
          },
          "value": "option1"
        },
        {
          "label": {
            "fr": "Option 2",
            "en": "Option 2",
            "es": "Opción 2",
            "ar": "خيار 2"
          },
          "value": "option2"
        },
        {
          "label": {
            "fr": "Option 3",
            "en": "Option 3",
            "es": "Opción 3",
            "ar": "خيار 3"
          },
          "value": "option3"
        }
      ]
    },
    {
      "key": "description",
      "personalized": false,
      "mandatory": false
    },
    {
      "key": "comments",
      "label": {
        "fr": "Comments",
        "en": "Comments",
        "es": "Comentarios",
        "ar": "تعليقات"
      },
      "type": "textarea",
      "mandatory": false,
      "personalized": false,
      "placeholder": {
        "fr": "Add comments...",
        "en": "Add comments...",
        "es": "Agregar comentarios...",
        "ar": "أضف تعليقات..."
      }
    }
  ]
}
```

### Validation and Best Practices

#### To Do

1. **Validate Your JSON** before putting it online
   - Check that there are no syntax errors

2. **Test with a Simple Case**
   - Start with a minimal configuration
   - Gradually add fields

3. **Use HTTPS URLs**
   - More secure for downloading icons
   - Avoids certificate issues

4. **Optimize Icons**
   - Recommended size: 200x200 pixels
   - PNG format with transparency if needed
   - Compress images to reduce loading time

5. **Complete Translations**
   - Provide translations for all supported languages (fr, en, es, ar)
   - Use consistent keys for values (`value`)

#### To Avoid

1. **Do Not Use Special Characters in Keys**
   - Good: `"key": "reference_number"`
   - Bad: `"key": "référence-n°"`

2. **Do Not Forget Required Properties**
   - `key` is always required
   - `options` is required for `dropdown`, `simpledropdown`, and `icons`

3. **Do Not Mix Types**
   - A field with `"type": "icons"` must have options with `icon`
   - A field with `"type": "text"` should not have `options`

4. **Do Not Use Invalid Icon URLs**
   - Verify that URLs are publicly accessible
   - Test URLs in a browser before using them

### Supported Language Codes

Translations use the following codes:
- `"fr"`: French
- `"en"`: English
- `"es"`: Spanish
- `"ar"`: Arabic

If a translation is missing for a language, the application will use the first available language or the field key.

### JSON File Hosting

**Hosting Options:**

1. **Classic Web Server**
   - Host the file on your web server
   - Ensure the file is publicly accessible
   - Example: `https://your-domain.com/config.json`

2. **Cloud Storage Services**
   - **GitHub**: Create a repository, add the file, use the raw URL
     - Example: `https://raw.githubusercontent.com/user/repo/main/config.json`
   - **Dropbox**: Share the file and use the direct link
   - **Google Drive**: Share publicly and use the direct link


### Other Settings Configuration

**Custom Field for JSON**
- Allows adding a custom field to every JSON output
- Enter the desired value in the text field
- The value is automatically saved

**User ID**
- Enter a user identifier (maximum 10 characters)
- Tap **"Save user ID"**
- This ID will be used in the tags of created cases

**Case Number**
- Allows resetting the case numbering counter
- Enter the new starting number
- Tap **"Save new number"**

**Email Address**
- Enter the destination email address for sending cases
- Tap **"Save email"**
- This address will be used when submitting cases
- **⚠️ Important for administrators:** This email address must be configured before agents can send cases by email. Without this configuration, the "Submit" button will not work correctly.

---

## Save and Submit Cases

There are **three methods** to manage your cases:
1. **Save locally**: Store the case on the device for later modification
2. **Submit by email**: Send an individual case by email
3. **Temporary export (USB)**: Export all cases to a computer (see dedicated section)

### Option 1: Save Locally

**When to use:**
- To save a case without sending it immediately
- To continue working on the case later
- To create multiple cases before submitting them

**How to do it:**
1. Take at least one photo
2. Fill in all required fields (defined in your JSON configuration)
3. Tap the **"Save"** button at the bottom of the screen
4. A confirmation notification appears
5. You are redirected to the home screen
6. The case is saved locally and can be viewed or modified later

**Characteristics:**
- The case is stored on your device
- You can modify it later
- No email sending is performed

### Option 2: Submit by Email

**When to use:**
- To send a complete case immediately by email
- To finalize a case and send it to the team
- To send an individual case quickly

**Prerequisites:**
- ⚠️ **A destination email address must be configured in settings** (Configuration tab > Email Address). This configuration is mandatory and must be done by the administrator before agents can use this feature.
- An email application must be installed on your device

**How to do it:**
1. Take at least one photo
2. Fill in all required fields (defined in your JSON configuration)
3. Tap the **"Submit"** button at the bottom of the screen
4. A loading indicator appears during preparation
5. The email application opens automatically with:
   - **Recipient**: The email address configured in settings
   - **Subject**: `[CASE]` followed by the case ID
   - **Attachment**: A ZIP file containing all case data (photos, metadata, JSON)
6. Verify the content and send the email

**ZIP File Contents:**
- All photos taken for the case
- A JSON file with all metadata:
  - Case ID
  - Tag (unique identifier)
  - Date and time
  - GPS coordinates (if available)
  - All filled fields (gender, age, description, types, etc.)
  - Custom fields if configured

**In Case of Error:**
- If no email application is installed: A message informs you
- If no email address is configured: A message asks you to configure the email in settings

### Going Back

If you tap the back button while creating a case:
- If the case is not empty, a confirmation will be requested
- You can:
  - **Cancel**: Continue modifying the case
  - **Confirm**: Abandon the case (all data will be deleted)

---

## View Existing Cases

### Accessing the Case List
1. On the home screen, tap the **"View cases"** button (folder icon with magnifying glass)
2. The list of all saved cases displays

### Case Display
Each case shows:
- **Tag**: The unique case identifier (at the top, large)
- **Date**: The case creation date
- **Preview**: A blurred image of the first photo
- **Instructions**:
  - "Click to edit or submit"
  - "Swipe left to delete"

### Available Actions

**Edit a Case**
1. Tap a case in the list
2. The form opens with all data pre-filled
3. Modify the desired fields
4. Tap **"Save"** or **"Submit"**

**Delete a Case**
1. Swipe the case to the left
2. A red delete button appears
3. Tap the delete button
4. Confirm deletion in the dialog box
5. The case and all its photos are permanently deleted

**Submit an Existing Case**
1. Open the case you want to submit
2. Verify that all information is correct
3. Tap **"Submit"**
4. The email opens with the case as an attachment

### Temporary Export (USB)

**When to use:**
- To export all cases at once to a computer
- To transfer cases via USB without Internet connection
- To create a complete backup of all your cases

**How to do it:**

1. **Access Export**
   - On the **"View cases"** screen, at the top of the list, you will find the **"Temporary export (USB)"** section

2. **Export All Cases**
   - Tap the **"Export all cases"** button (with the number of cases in parentheses)
   - A progress indicator appears during export
   - Each case is converted to a ZIP file containing:
     - All photos from the case
     - A JSON file with all metadata

3. **Access Exported Files**

   **On Android:**
   - A folder selector opens automatically
   - Choose where to save the files (for example: a folder on your phone or a USB drive)
   - Files are copied to the selected folder
   - Files are available in the chosen folder
   - **Important**: Export expires after 30 minutes

   **On iOS:**
   - Files are exported to the application folder
   - To access the files:
     1. Connect your iPhone to your Mac or PC
     2. Open **Finder** (Mac) or **iTunes** (PC)
     3. Select your iPhone
     4. Go to **"Files"** > **"Divi"**
     5. Download the **"TempExport"** folder
   - **Important**: Export expires after 30 minutes

4. **Export Status**
   - Once export is complete, you will see:
     - **"Export active"** with a remaining time counter
     - The number of exported files
     - A button to delete the export

5. **Delete Export**
   - If you want to delete the export before it expires:
     - Tap the **"Delete export"** button
     - Confirm deletion
     - Temporary files are deleted

**Export Characteristics:**
- Exports **all** saved cases at once
- Each case is in a separate ZIP file
- Same format as email export (photos + JSON)
- Automatic expiration after 30 minutes
- Files can be transferred to a computer

**In Case of Error:**
- If no cases are available: A message informs you there is nothing to export
- If export fails: An error message appears, try again

### Statistics on Home Screen
At the bottom of the home screen, you can see:
- **Number of cases**: Total number of saved cases
- **Number of photos**: Total number of photos taken

---

## Application Settings

### Accessing Settings
Tap the **Settings** icon in the top right of the home screen.

### "Preferences" Tab

**Dark Mode**
- Enable or disable dark mode
- Change is immediate

**Language**
- Select the interface language from available options
- Available languages depend on the application configuration

### "Configuration" Tab (Admin)

See the [Load Configuration in Settings](#load-configuration-in-settings) section for details.

**Additional Actions:**

**Clear Data**
- Deletes all saved cases and photos
- **Warning**: This action is irreversible
- Confirmation is requested before deletion

**Documentation**
- Opens the complete application documentation
- Useful for understanding configuration formats and advanced features

---

## Recovery After Crash

If the application closes unexpectedly while creating a case:

1. Upon reopening, if unsaved photos are detected, an alert appears
2. You can choose:
   - **Recover**: Photos are loaded into a new case that you can complete
   - **Delete**: Unsaved photos are permanently deleted

---

## Tips and Best Practices

### For Better Documentation
- Take at least 5 photos from different angles (required)
- Always fill in the description with relevant details (if the field is present in your configuration)
- Ensure GPS location is enabled for automatic geolocation
- Verify that all required fields (defined in your JSON configuration) are filled before submitting

### Configuration
- Test your configuration with a test case before using it in production
- Verify that the configuration URL is accessible from your device
- Configure the destination email address before submitting cases

*Last updated: Version 1.0.0*

