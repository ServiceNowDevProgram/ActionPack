# KB Broken Link Checker

### Summary
Detects **broken HTTP/HTTPS links** inside ServiceNow Knowledge Base articles.  
Returns a list of affected KBs and their problematic URLs.

### Inputs
| Name | Type | Description | Default |
|------|------|-------------|----------|
| `kb_query` | String | Encoded query for filtering KB articles | `active=true^published=true` |
| `max_articles` | Integer | Number of articles to scan | 100 |
| `timeout_seconds` | Integer | Timeout per request | 5 |

### Outputs
| Name | Type | Description |
|------|------|-------------|
| `broken_links` | Array | Array of `{article_sys_id, article_number, article_title, bad_url, http_status}` |
| `count_broken` | Integer | Total broken links found |

### Example Flow Usage
1. Drag the **KB Broken Link Checker** action into your flow.  
2. Set `kb_query = active=true^published=true^category=IT`.  
3. Run it — outputs will show all invalid links with HTTP status codes.  
4. You can chain it with an email notification or table insert to track issues.

### Test Scenario
1. Create a KB article with a bad link like `http://example.invalid/test`.  
2. Run the action with `max_articles=10`.  
3. Verify output contains:
   ```json
   {
     "article_number": "KB0010001",
     "bad_url": "http://example.invalid/test",
     "http_status": "Error: ..."
   }
