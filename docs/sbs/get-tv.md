## Endpoint Summary

**URL:** `/main-api/section/tv`  
**Method:** `GET`  
**Description:** This endpoint retrieves a list of TV programs filtered by section (pgm_sct), sorting method (sort), and pagination (offset, limit).

---

## Response

### Example Response Body

**Request URL:**

```
https://apis.sbs.co.kr/main-api/section/tv?pgm_sct=DR&sort=new&offset=0&limit=1

 ```

**Response (JSON):**

``` JSON
[
  {
    "pgm_id": "P473139476",
    "title": "귀궁",
    "pgm_nm": "귀궁",
    "link_url": "https://programs.sbs.co.kr/drama/hauntedpalace",
    "pgm_img_url": "https://img2.sbs.co.kr/img/sbs_cms/WE/2025/03/26/wZj1742944148145-600-847.jpg",
    "m_img_url": "https://img2.sbs.co.kr/img/sbs_cms/WE/2025/03/26/wZj1742944148145-600-847.jpg",
    "new_yn": "N",
    "free_part_yn": "",
    "brd_state": "",
    "link_new_yn": "N"
  }
]

 ```

### Field Descriptions

| Field | Type | Description |
| --- | --- | --- |
| `pgm_id` | string | Unique program identifier |
| `title` | string | Program title (usually in Korean) |
| `pgm_nm` | string | Program name (same as title, sometimes used for display) |
| `link_url` | string | URL to the program’s official page |
| `pgm_img_url` | string | URL of the program’s main image (poster/banner) |
| `m_img_url` | string | URL of a mobile-optimized image for the program |
| `new_yn` | string | Indicates if the program is new (`Y` for yes, `N` for no) |
| `free_part_yn` | string | Undocumnted |
| `brd_state` | string | Undocumnted |
| `link_new_yn` | string | Undocumnted (`Y` or `N`) |

---

## Notes

- The title and pgm_nm in response have usually the same value
    
- free_part_yn and brd_state have an empty string as value most of the time