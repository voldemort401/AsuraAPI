# AsuraAPI
I discovered the official asurascans API that the website uses this is my attempt at documenting the API's endpoints.

I discovered the official asurascans API that the website uses this is my attempt at documenting the API's endpoints.

## Endpoints
- Check status
- Count the number of comments
- Get the Reaction counts on chapters
- Get the Reaction counts on series
- Get the comments on a chapter
- Get the comments on the series page
- Get the emojis
- Get user details
- Get leaderboard

### Check status
- **Method** = `GET`
- **Path** = `api/guilds/status`

```

╰─❯ curl https://api.asurascans.com/api/guilds/status                                       
{"data":{"public":true,"visible":true}}

```

### Count the number of comments
- Method: get
- path: api/chapters/_chapter_id_/comments/count
```
// Response
{
	"total" : integer
}
```

```
// comment count for copying skills with affinity chapter 8
╰─❯ curl https://api.asurascans.com/api/chapters/261928/comments/count
{"total":283}
```

### Get the Reaction counts on chapters 
- Method: get
- path: api/chapters/_chapter_id_/reactions

``` 
// Response
{
  "data": {
    "reaction_counts": {
      "angry": integer,
      "funny": integer,
      "love": integer,
      "sad": integer,
      "surprised": integer,
      "upvote": integer
    },
    "user_reaction": "love | funny | upvote | suprised | angry | sad" | null
  }
}
```

```
// reactions count for copying skills with affinity chapter 8              
╰─❯ curl https://api.asurascans.com/api/chapters/261928/reactions                                                             
{"data":{"reaction_counts":{"angry":11,"funny":97,"love":767,"sad":12,"surprised":17,"upvote":41},"user_reaction":null}}
```

### Get the Reaction counts on series

- Method: get
- path: api/series/_series_id_/reactions

``` 
// Response
{
  "data": {
    "reaction_counts": {
      "angry": integer,
      "funny": integer,
      "love": integer,
      "sad": integer,
      "surprised": integer,
      "upvote": integer
    },
    "user_reaction": "love | funny | upvote | suprised | angry | sad" | null
  }
}
```

```
// reactions count for copying skills with affinity              
╰─❯ curl https://api.asurascans.com/api/series/6095/reactions                                                       
{"data":{"reaction_counts":{"angry":11,"funny":26,"love":282,"sad":15,"surprised":17,"upvote":47},"user_reaction":null}}
```

### Get the comments
- method: get
- path: api/chapters/_chapter_id_/comments
- **Options**:
- ```
	sort = newest | oldest | top 
	limit = integer
	offset = integer | determines how many comments to skip returning 
  ```

``` 
// Response
{
	"data":[
		{
			"content": "Content of the comment",
			"created_at": "YYYY-MM-DDTHH:MM:SS.ffffffZ",
			"downvotes": integer, 
			"gif_url": "URL" | null, 
			"id": comment_id_integer, 
			"is_edited": true | false, 
			"is_pinned": true | false, 
			"media_urls": ["URL"] | null,
		    "pin_kind": "pinned",
		    "replies": [
			    {
				    "content": "Content of the comment",
			        "created_at": "YYYY-MM-DDTHH:MM:SS.ffffffZ",
			        "downvotes": integer,
			        "gif_url": "URL" | null,
			        "id": reply_id_integer,
			        "is_edited": true | false,
			        "is_pinned": true | false,
		            "media_urls": ["URL"] | null,
			        "pin_kind": "pinned",
		            "reply_count": 0,
			        "upvotes": integer,
			        "user": 
			        {
			            "alltime_rank": "the all time rank   (integer)",
			            "comment_rank": "current season rank (integer)",
			            "guild_badge_icon": "guild_icon | EMPTY STRING",
			            "guild_color": "HEX_COLOR_CODE  | EMPTY STRING ",
			            "guild_tag": "guild_tag | EMPTY STRING",
			            "id": user_id_integer,
			            "is_beta_user": true | false,
			            "is_premium": true | false,
			            "profile_picture_url": "URL",
			            "role": "premium | user",
			            "username": "user_name"
				    },
			        "user_vote": null
			    }
		    ],
		    "reply_count": integer,
		    "upvotes": integer,
		    "user":
		    {
			    "alltime_rank": integer,
		        "comment_rank": integer,
		        "guild_badge_icon": "",
		        "guild_color": "",
		        "guild_tag": "",
		        "id": user_id,
		        "is_beta_user": true | false,
		        "is_premium": true | false,
		        "profile_picture_url": "empty string if no profile pic",
		        "role": "user | premium",
		        "username": "user_name"
		    },
		    "user_vote": null
		}
	],
	
	"meta": 
	{
	    "has_more": true | false,
	    "total": integer
	},
    "success": true
}
```

### Get the comments on the series page
- method: get
- path: /api/series/_series_id_/comments
**Options**:
- ```
	sort = newest | oldest | top 
	limit = integer
	offset = integer | determines how many comments to skip returning 
  ```


``` 
// Response
{
	"data":[
		{
			"content": "Content of the comment",
			"created_at": "YYYY-MM-DDTHH:MM:SS.ffffffZ",
			"downvotes": integer, 
			"gif_url": "URL" | null, 
			"id": comment_id_integer, 
			"is_edited": true | false, 
			"is_pinned": true | false, 
			"media_urls": ["URL"] | null,
		    "pin_kind": "pinned",
		    "replies": [
			    {
				    "content": "Content of the comment",
			        "created_at": "YYYY-MM-DDTHH:MM:SS.ffffffZ",
			        "downvotes": integer,
			        "gif_url": "URL" | null,
			        "id": reply_id_integer,
			        "is_edited": true | false,
			        "is_pinned": true | false,
		            "media_urls": ["URL"] | null,
			        "pin_kind": "pinned",
		            "reply_count": 0,
			        "upvotes": integer,
			        "user": 
			        {
			            "alltime_rank": "the all time rank   (integer)",
			            "comment_rank": "current season rank (integer)",
			            "guild_badge_icon": "guild_icon | EMPTY STRING",
			            "guild_color": "HEX_COLOR_CODE  | EMPTY STRING ",
			            "guild_tag": "guild_tag | EMPTY STRING",
			            "id": user_id_integer,
			            "is_beta_user": true | false,
			            "is_premium": true | false,
			            "profile_picture_url": "URL",
			            "role": "premium | user",
			            "username": "user_name"
				    },
			        "user_vote": null
			    }
		    ],
		    "reply_count": integer,
		    "upvotes": integer,
		    "user":
		    {
			    "alltime_rank": integer,
		        "comment_rank": integer,
		        "guild_badge_icon": "",
		        "guild_color": "",
		        "guild_tag": "",
		        "id": user_id,
		        "is_beta_user": true | false,
		        "is_premium": true | false,
		        "profile_picture_url": "empty string if no profile pic",
		        "role": "user | premium",
		        "username": "user_name"
		    },
		    "user_vote": null
		}
	],
	
	"meta": 
	{
	    "has_more": true | false,
	    "total": integer
	},
    "success": true
}
```


### Get Emojis
- method: get
- path: /api/emojis
```
// Response
{
	"data": 
	[
		{
			"name": "name",
			"url": "url",
			"animated": true | false
		} 	
	]
}
```

```
// example

╰─❯ curl https://api.asurascans.com/api/emojis           
{"data":[{"name":"admin","url":"https://cdn.asurascans.com/asura-images/emojis/admin.1790616921654826824.webp","animated":false},{"name":"angryy","url":"https://cdn.asurascans.com/asura-images/emojis/angryy.1790616922289227702.webp","animated":false}]
}
```


### Get user details
- method: get
- path:/api/user/username

```
{
  "data": {
    "achievements": [
      "string"
    ],
    "alltime_rank": integer,
    "banner_url": "URL",
    "bookmarks": [
      {
        "chapter_count": integer,
        "cover_url": "string",
        "slug": "string",
        "status": "string",
        "title": "string",
        "type": "string"
      }
    ],
    "chapters_read": integer,
    "comment_count": integer,
    "comment_rank": integer,
    "created_at": "YYYY-MM-DDTHH:MM:SS.ffffffZ",
    "description": "description of the manhwa",
    "favorite_series": [
      {
        "cover_url": "string",
        "id": integer,
        "position": integer,
        "slug": "string",
        "status": "status of the series ongoing | completed | hiatus",
        "title": "string",
        "type": "string"
      }
    ],
    "guild": {
      "badge_icon": "string",
      "color": "string",
      "icon_url": "string",
      "member_count": integer,
      "name": "string",
      "role": "string",
      "tag": "string"
    },
    "has_more_activity": true | false,
    "has_more_bookmarks": true | false,
    "has_premium": true | false,
    "hide_activity": true | false,
    "hide_bookmarks": true | false,
    "hide_comments": true | false,
    "hide_profile_content": true | false,
    "id": integer,
    "is_beta_user": true | false,
    "is_own_profile": true | false,
    "karma": "all the aura since day 1",
    "last_read": [
      {
        "chapter_number": integer,
        "chapter_title": "string",
        "read_at": "YYYY-MM-DDTHH:MM:SS.ffffffZ",
        "series_cover": "URL",
        "series_slug": "string",
        "series_title": "string"
      }
    ],
    "profile_picture_url": "string",
    "role": "string",
    "season": {
      "key": "current season example 2026-Q4",
      "number": "The season number(integer)",
      "label": "string",
      "starts_at": "YYYY-MM-DDTHH:MM:SS.ffffffZ",
      "ends_at": "YYYY-MM-DDTHH:MM:SS.ffffffZ"
    },
    "season_history": [
      {
        "key": "The season example 2026-Q3",
        "number": "The season number(integer)",
        "label": "string",
        "rank": integer,
        "aura": integer
      }
    ],
    "season_karma": "Current season aura dk why its called karma instead",
    "total_activity": "amount of chapters read until 3 days ago(integer)",
    "total_bookmarks": integer,
    "username": "string"
  }
}

```

### Get Leader board
- method: get
- path: api/leaderboard
```
// Response
{
  "data": 
  [
    {
      "rank": integer,
      "id": user_id_integer,
      "username": "string",
      "profile_picture_url": "URL",
      "role": "user | premium",
      "has_premium": true | false,
      "karma": aura_integer,
      "comment_count": integer
    },
  ]
```

- It gives the top 100 users of the current season
