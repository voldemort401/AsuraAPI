# AsuraAPI
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
- Get all the artist and authors that have their works on asura 
- Search

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

### Get all the artist and authors that have their works on asura
- method: get
- path: api/creators

```
//Response
{
	"data" : {
		"artists": [
			"artist1", "artist2", ...
		],
		"authors": [
			"author1", "author2", ...
		]
	}
}
```

### Search
- method: get
- path:api/search
- #### Options

```
q = manhwa_name 
limit = integer 


if q is not specified it will return the manhwas in order of how they appear in the websites "Latest Updates" section
```

```
// Response
{
	"data": [
		{
			"id": integer,
			"slug": "string",
			"title": "string",
			"alt_titles": [
				"This field wont exist if there is no alternative title"
			], 
			"description": "<p>desc</p>",
			"cover": "URL", 
			"banner": "URL", 
			"status": "ongoing | completed | hiatus | axed | dropped",
			"type": "ive seen manhua and manhwa",
			"author": "string",
			"artist": "string",
			"popularity_rank": integer,
			"bookmar_count": integer,
			"rating": float,
			"chapter_count": integer,
			"last_chapter_at": "YYYY-MM-DDTHH:MM:SS.ffffffZ",
			"created_at": "YYYY-MM-DDTHH:MM:SS.ffffffZ",
			"updated_at": "YYYY-MM-DDTHH:MM:SS.ffffffZ",
			"public_url": "/{type}/{title}",
			"source_url": "/s/{id}",
			"genres": [
				{
					"id": id_of_the_genre_integer,
					"name": "string",
					"slug": "string"
				}, // and so on for other generes
			],
			"latest_chapters": [
				{
					"id": chapter_id,
					"series_id": 0,
					"number": chapter_number
				},
				{
					"id": chapter_id,
					"series_id": 0,
					"number": chapter_number
				},
				{
					"id": chapter_id,
					"series_id": 0,
					"number": chapter_number
				}
			]
		}
	],
	"meta": {
	    "total": integer,
	    "per_page": integer // ive only seen this value be 20
    }
}
```

```
// example
╰─❯ curl 'https://api.asurascans.com/api/search?q=%20Rise%20of%20The%20Cheat%20User'
{
  "data": [
    {
      "id": 2092,
      "slug": "rise-of-the-cheat-user",
      "title": "Rise of The Cheat User",
      "alt_titles": [
        "大数据世界",
        "万年を生きるチートゲーマー、嫁たちと異世界バトル",
        "World of Data",
        "Great Data World",
        "Kai Gua Wanjia Cong 0 Shengji",
        "开挂玩家从0升级"
      ],
      "description": "Sun Ran, who was born in a slum, was a master at cheating in games. Under the guise of a myriad of identities, he traversed carefree through countless virtual words. Unexpectedly, he was kicked out of the virtual worlds by an Enforcer, and found himself riddled with a hefty debt of 900 million in the real world. In order to pay off the debt, Sun Ran made a deal with the Central AI and became an Enforcer himself. Thus began his fierce battle against the 'Destroyers', players who cheated in their gameplay.",
      "cover": "https://cdn.asurascans.com/asura-images/covers/rise-of-the-cheat-user.758744.webp",
      "status": "dropped",
      "type": "manhua",
      "author": "Mo Xiang",
      "artist": "Kuaikan",
      "popularity_rank": 347,
      "bookmark_count": 343,
      "rating": 7.333333333333333,
      "chapter_count": 21,
      "last_chapter_at": "2023-01-24T23:32:31Z",
      "created_at": "0001-01-01T00:00:00Z",
      "updated_at": "2026-10-04T07:55:37.941347Z",
      "public_url": "/comics/rise-of-the-cheat-user-3ec3b16f",
      "source_url": "/s/2092",
      "genres": [
        {
          "id": 1,
          "name": "Action",
          "slug": "action"
        },
        {
          "id": 16,
          "name": "Fantasy",
          "slug": "fantasy"
        },
        {
          "id": 18,
          "name": "Game",
          "slug": "game"
        },
        {
          "id": 55,
          "name": "Shounen",
          "slug": "shounen"
        },
        {
          "id": 63,
          "name": "System",
          "slug": "system"
        }
      ],
      "latest_chapters": [
        {
          "id": 150689,
          "series_id": 0,
          "number": 21,
          "slug": "c9c852ee-7617-44c2-964d-aa2b7f6ab1ee",
          "page_count": 0,
          "is_premium": false,
          "comments_enabled": false,
          "published_at": "2023-01-24T23:32:31Z",
          "view_count": 0,
          "created_at": "0001-01-01T00:00:00Z"
        },
        {
          "id": 150688,
          "series_id": 0,
          "number": 20,
          "slug": "0767c600-e85c-41cd-8fd3-e4c052c33420",
          "page_count": 0,
          "is_premium": false,
          "comments_enabled": false,
          "published_at": "2023-01-15T21:19:17Z",
          "view_count": 0,
          "created_at": "0001-01-01T00:00:00Z"
        },
        {
          "id": 150687,
          "series_id": 0,
          "number": 19,
          "slug": "d975ccd6-08ce-4097-9bcf-6815dcd5dc2f",
          "page_count": 0,
          "is_premium": false,
          "comments_enabled": false,
          "published_at": "2023-01-10T22:38:31Z",
          "view_count": 0,
          "created_at": "0001-01-01T00:00:00Z"
        }
      ]
    }
  ],
  "meta": {
    "total": 1,
    "per_page": 20
  }
}
```
