# Setting Up OTA JSON and Adding a New Maintainer/Device  

## OTA JSON Format  

To setup updates, you need to provide a JSON file named after your device (e.g., device.json), following this structure:

```device.json
{
  "response": [
    {
      "datetime": 1230764400,
      "filename": "ota-package.zip",
      "id": "5eb63bbbe01eeed093cb22bb8f5acdc3", //md5
      "romtype": "OFFICIAL",
      "size": 314572800, // size in bytes
      "url": "https://example.com/ota-package.zip",
      "version": "1.1"
    }
  ]
}
```

### Attribute Details  

| Attribute  | Description  |
|------------|-------------|
| `datetime`  | Build date as a UNIX timestamp.  |
| `filename`  | The name of the update package file.  |
| `id`  | A unique identifier for the update.  |
| `romtype`  | The release type (e.g., `OFFICIAL`), compared with `ro.lineage.releasetype`.  |
| `size`  | The update file size in bytes.  |
| `url`  | Direct URL to the update package.  |
| `version`  | The build version, compared with `ro.lineage.build.version`.  |

Ensure that the JSON file is hosted at an accessible URL and follows this format exactly to avoid update errors.  

---

## Adding a New Maintainer & Device  

Each device must be registered with its correct codename and assigned a maintainer.  

### Requirements:  

- **Device Codename**: Must match the official device codename (e.g., `Pixel 6` → `oriole`).  
- **Maintainer Name**: Must match the `AXION_MAINTAINER` string defined in the build environment.  

### Steps to Add a Device:  

1. **Register the device codename** in the OTA JSON structure.  
2. **Ensure the maintainer’s name** is correctly set in `AXION_MAINTAINER`.  
3. **Push changes** with the updated JSON file and updated maintainer/device list (for initial setup).  
