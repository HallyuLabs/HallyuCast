**Endpoint:**  
`https://static.apis.sbs.co.kr/program-api/1.0/menu/:id`

**Method:** `GET`

**Description:**

Fetches metadata and menu configuration for a specific SBS program. This includes the program title, image assets, channel information, and detailed menus (such as introduction, cast, videos, clips, photo viewers, and events).

---

## 🔗 URL Parameters

| Parameter | Description | Example |
| --- | --- | --- |
| `:id` | Program ID (e.g., SBS VOD ID) | `P473139482` |

---

## 🧾 Example Request

``` http
GET https://static.apis.sbs.co.kr/program-api/1.0/menu/springofyouth

 ```

---

## ✅ Success Response

### Response Structure

``` json
{
  "program": { ... },
  "custom": { ... },
  "menus": [ ... ]
}

 ```

---

### `program` object

| Field | Description |
| --- | --- |
| `programid` | Program ID (matches the `:id`) |
| `programcd` | Program short code (e.g. "springofyouth") |
| `fullprogramid` | Channel-prefixed program ID |
| `vodid` | VOD ID, same as `programid` |
| `channelid` | Channel ID (e.g., "S01") |
| `channelname` | Channel display name (empty sometimes) |
| `category` | Category code (e.g., "T" for drama) |
| `title` | Full title of the program |
| `broadstate` | Broadcast status ("방영중" = On Air) |
| `color` | Hex color used for UI theming |
| `circleimg` | Circular thumbnail image URL |
| `shareimg` | Image used for social sharing |
| `template_main_url` | Full SBS program page |
| `template_section` | Program genre/type (e.g., "drama") |
| `isbroad` | Boolean flag for current broadcasting |
| `subtitle_yn` | Subtitle availability ("Y"/"N") |
| `menu_programs` | List of related programs (optional) |

---

### `menus` array

Each item in the array represents a menu tab shown on the program page (e.g., Program Info, Cast, VODs, Clips).

| Field | Description |
| --- | --- |
| `mnuid` | Menu unique ID |
| `menuname` | Display name of the menu |
| `menuurl` | Full URL to access the menu |
| `menuord` | Display order |
| `menutype` | Type of content (`T1`, `T2`, `T3`, `T4`) |
| `submenus` | Nested submenus (same structure as `menus`) |
| `banner` | Optional banner (title, image, link) |
| `photo` | Photo module details (if type is "photo") |
| `popup_size` | Size for popup menus (if `is_popup: true`) |
| `visible` | Whether this menu should be displayed |

---

### Example Menu Entry

``` json
{
  "menuname": "등장인물",
  "menuurl": ",https://programs.sbs.co.kr/drama/springofyouth/about/84616"
  "menutype": "T3",
  "submenus": [
    {
      "menuname": "등장인물",
      "menuurl": "https://programs.sbs.co.kr/drama/springofyouth/cast/86365"
    },
    {
      "menuname": "인물관계도",
      "menuurl": "https://programs.sbs.co.kr/drama/springofyouth/basicinfo/86366"
    }
  ]
}

 ```

---

## 🔎 Notes

- `menutype` roughly maps to:
    
    - `T1`: Static/standard content (like About, Clips, VODs)
        
    - `T2`: Event-based or dynamic module (like event pages or photo viewers)
        
    - `T3`: Grouped content with submenus (e.g., Cast + Relationships)
        
    - `T4`: External module or popup (e.g., TALK)
        
- `submenus` are common in cast or relationship menus.
    
- `photo.module_id` and `photo.display_type` are used for dynamic photo viewers and galleries.
    
- If `isbroad` is `false`, the drama is no longer airing.