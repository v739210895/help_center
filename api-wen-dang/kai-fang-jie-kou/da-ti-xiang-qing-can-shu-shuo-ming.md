# 答题详情示例及说明

## **答题数据列表（批量查询）**

```cpp
//https://survey.imur.tencent.com/open/v1/answers/60ebdefe76051f6b8a37f782?sign=cf8197406494facd323b50de97f3f3ba&timestamp=1631268187
//示例

//sign生成（md5）appSecretiamsecretsid60ebdefe76051f6b8a37f782timestamp1631268187
//时间戳有时效性，失效了就更新时间戳重新计算sign

//仅返回有答案的题目
{
	"data": {
		"total": 1,
		//查询数量
		"list": [{
			"_id": "613b1ea70bebcc94cec7f5bc",
			//答卷编号，aid
			"ip": "127.0.0.1",
			"client_id": "1226565806200979456",
			//浏览器编号
			"user_agent": "Mozilla\/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit\/537.36 (KHTML, like Gecko) Chrome\/92.0.4515.159 Safari\/537.36",
			//设备信息
			"started_at": 1631264344,
			//开始答题时间
			"ended_at": 1631264423,
			//结束答题时间
			"answer_consumed": 79,
			//答题时长：秒
			"answers": [{
				//答案列表
				"id": "ZWF2",
				//题目id
				"type": "radio",
				//题型
				"options": [{
					//选项
					"id": "AFA5",
					//选项id
					"text": "<p>社交观光团——注重与朋友的互动交流，享受在对局中自由探索，一路打闹一路躺赢<\/p>"
					//选项内容
				}]
			}, {
				"id": "KYJ6",
				"type": "radio",
				"options": [{
					"id": "EYW8",
					"text": "<p>2-比较不满意<\/p>"
				}]
			}, {
				"id": "IJDc",
				"type": "radio",
				"options": [{
					"id": "HVAe",
					"text": "<p>2-比较不满意<\/p>"
				}]
			}, {
				"id": "DJDl",
				"type": "select",
				"options": [{
					"id": "VPTs",
					"text": "18"
				}]
			}, {
				"id": "WY1i",
				"type": "checkbox",
				"options": [{
					"id": "HG1m",
					"text": "<p>手机游戏（含平板电脑）<\/p>"
				}, {
					"id": "RN1l",
					"text": "<p>网页游戏<\/p>"
				}]
			}, {
				"id": "AB1q",
				"type": "checkbox",
				"options": [{
					"id": "NG1t",
					"text": "<p>棋牌类游戏（如 QQ游戏大厅、联众游戏平台、JJ比赛等平台上的棋牌游戏）<\/p>"
				}, {
					"id": "YX1r",
					"text": "<p>大型客户端游戏（需要安装客户端，上网登录才能玩的大型客户端游戏，如 英雄联盟LOL、魔兽世界、穿越火线、守望先锋、梦幻西游、地下城与勇士、绝地求生、QQ炫舞等）<\/p>"
				}]
			}, {
				"id": "QJ1x",
				"type": "checkbox",
				"options": [{
					"id": "WK21",
					"text": "<p>【画面音乐】高质量的感官体验（如精致好看的画面\/画风、好听的音乐\/音效等）<\/p>"
				}, {
					"id": "WD20",
					"text": "<p>【策略思考】需要思考和策略能力的玩法<\/p>"
				}]
			}, {
				"id": "NO2e",
				"type": "checkbox",
				"options": [{
					"id": "HZ2l",
					"text": "<p>B--变形金刚<\/p>"
				}, {
					"id": "VR2k",
					"text": "<p>B--崩坏3（PC端）<\/p>"
				}, {
					"id": "OC2j",
					"text": "<p>B--堡垒之夜<\/p>"
				}]
			}, {
				"id": "YH44",
				"type": "checkbox",
				"options": [{
					"id": "OY4e",
					"text": "<p>视频网站：B站、腾讯视频、爱奇艺等<\/p>"
				}, {
					"id": "GI4c",
					"text": "<p>微信订阅号\/公众号\/视频号：游戏公众号或视频号等<\/p>"
				}, {
					"id": "WI4b",
					"text": "<p>应用商店中的游戏内容版块：TAPTAP、应用宝等<\/p>"
				}, {
					"id": "GU49",
					"text": "<p>社交网站：微博、小红书、QQ好友动态、兴趣部落、游戏圈子等<\/p>"
				}, {
					"id": "YP48",
					"text": "<p>大型论坛贴吧中的游戏吧或版块：百度贴吧、豆瓣、知乎等<\/p>"
				}, {
					"id": "WC4k",
					"text": "<p>王者荣耀手机端端官方网站<img src=\"https:\/\/mur-survey-1255655535.file.myqcloud.com\/static_files\/images\/5Lw7H8bhX5kAsdMGF6dsv5NLgmJEfN6HflSsHTpU.png?imageMogr2\/thumbnail\/512x&amp;width=512&amp;height=724\"><\/p>"
				}, {
					"id": "HI4j",
					"text": "<p>王者荣耀电脑端官方网站<img src=\"https:\/\/mur-survey-1255655535.file.myqcloud.com\/static_files\/images\/e64q3WclxWyXmjwZagn2CKTrcOCFlySFDVaXmMg9.png?imageMogr2\/thumbnail\/512x&amp;width=512&amp;height=724\"><\/p>"
				}]
			}, {
				"id": "PA4p",
				"type": "subjective",
				"text": "开放题"
			}, {
				"id": "SG4t",
				"type": "range",
				"value": 3
			}, {
				"id": "UQ86",
				"type": "range",
				"value": 5
			}, {
				"id": "LJ4w",
				"type": "matrixRadio",
				"groups": {
					"OM53": [{
						"id": "AG4y",
						"text": "<p>2-比较不满意<\/p>"
					}],
					"VT54": [{
						"id": "JQ4z",
						"text": "<p>3-一般<\/p>"
					}],
					"MC55": [{
						"id": "ON50",
						"text": "<p>4-比较满意<\/p>"
					}],
					"KI58": [{
						"id": "ON50",
						"text": "<p>4-比较满意<\/p>"
					}],
					"BO5a": [{
						"id": "ON50",
						"text": "<p>4-比较满意<\/p>"
					}],
					"WK56": [{
						"id": "ON50",
						"text": "<p>4-比较满意<\/p>"
					}],
					"SP57": [{
						"text": "<p>4-比较满意<\/p>",
						"id": "ON50"
					}],
					"KC59": [{
						"text": "<p>4-比较满意<\/p>",
						"id": "ON50"
					}],
					"SJ5b": [{
						"id": "ON50",
						"text": "<p>4-比较满意<\/p>"
					}]
				}
			}, {
				"id": "VU5c",
				"type": "matrixRadio",
				"groups": {
					"ZM5g": [{
						"id": "BN5e",
						"text": "<p>偶尔会玩一下<\/p>"
					}],
					"PV5h": [{
						"text": "<p>偶尔会玩一下<\/p>",
						"id": "BN5e"
					}]
				}
			}, {
				"id": "UF5i",
				"type": "matrixRadio",
				"groups": {
					"HB5t": [{
						"id": "LH5n",
						"text": "<p>非常满意<\/p>"
					}],
					"QK5q": [{
						"id": "ZX5m",
						"text": "<p>比较满意<\/p>"
					}],
					"BZ5r": [{
						"id": "LH5n",
						"text": "<p>非常满意<\/p>"
					}],
					"KP5s": [{
						"id": "LH5n",
						"text": "<p>非常满意<\/p>"
					}]
				}
			}, {
				"id": "ZS5w",
				"type": "matrixCheckbox",
				"groups": {
					"SO68": [{
						"id": "AD60",
						"text": "<p>是喜欢的选手\/大神\/创作者发的内容<\/p>"
					}, {
						"id": "UV61",
						"text": "<p>是喜欢的英雄相关的内容<\/p>"
					}],
					"HI69": [{
						"id": "PW5z",
						"text": "<p>内容质量高（有创意、操作优秀、讲解清晰等）<\/p>"
					}],
					"NP6a": [{
						"text": "<p>是喜欢的选手\/大神\/创作者发的内容<\/p>",
						"id": "AD60"
					}],
					"WJ6b": [{
						"id": "AD60",
						"text": "<p>是喜欢的选手\/大神\/创作者发的内容<\/p>"
					}],
					"ZV6d": [{
						"id": "AD60",
						"text": "<p>是喜欢的选手\/大神\/创作者发的内容<\/p>"
					}],
					"NZ6h": [{
						"id": "BU64",
						"text": "<p>作品\/意见征集活动<\/p>"
					}],
					"AK6e": [{
						"id": "UV61",
						"text": "<p>是喜欢的英雄相关的内容<\/p>"
					}],
					"XF6c": [{
						"id": "AD60",
						"text": "<p>是喜欢的选手\/大神\/创作者发的内容<\/p>"
					}],
					"PJ6f": [{
						"text": "<p>是喜欢的英雄相关的内容<\/p>",
						"id": "UV61"
					}],
					"HG6g": [{
						"text": "<p>可以得到福利奖励<\/p>",
						"id": "GP63"
					}]
				}
			}, {
				"id": "EG7m",
				"type": "cascade",
				"options": [{
					"id": "130000",
					"name": "河北省"
				}, {
					"id": "130400",
					"name": "邯郸市"
				}, {
					"id": "130408",
					"name": "永年区"
				}],
				"subTitles": [{
					"id": "ZR87",
					"text": "省"
				}, {
					"id": "ZY88",
					"text": "市"
				}, {
					"id": "DM89",
					"text": "区"
				}]
			}, {
				"id": "RG7t",
				"type": "matrixRange",
				"groups": {
					"XD7u": 2,
					"LG7v": 6,
					"UM7w": 5,
					"UG7x": 4
				}
			}, {
				"id": "XR8d",
				"type": "matrixRange",
				"groups": {
					"XD7u": 3
				}
			}, {
				"id": "VJ80",
				"type": "attachment",
				"options": [{
					"text": "https:\/\/mur-private-assets-1255655535.file.myqcloud.com\/survey\/de088ede01fe58ddd43f815bb7f7af21_1631264416.jpg"
				}, {
					"text": "https:\/\/mur-private-assets-1255655535.file.myqcloud.com\/survey\/76aa2f08123cce11cb31bc67b1b31550_1631264416.jpg"
				}, {
					"text": "https:\/\/mur-private-assets-1255655535.file.myqcloud.com\/survey\/1a24dd14fa93921a27343dee523b0150_1631264416.png"
				}]
			}, {
				"id": "UND2",
				"type": "sort",
				"groups": {
					"VXK5": 2,
					"NRY8": 3,
					"TTU7": 4,
					"NLL3": 5,
					"FVF4": 6,
					"SHX6": 1
				}
			}],
			"abnormal_end": false,
			//是否非正常结束
			"answer_finished": true,
			//答题状态，true=已完成，false=未完成
			"user_type": "weak_third_party",
			//用户ID类型
			"uid": "testid",
			//用户ID
			"uid_info": "testinfo",
			//自定义内容
			"channel": "-",
			//来源平台
			"created_at": "2021-09-10 17:00:23",
			"updated_at": "2021-09-10 17:00:23",
			"device": "other",
			"nation": "",
			//国家或地区
			"browser": "Chrome",
			//浏览器类型
			"source": "other",
			//用户ID渠道，wx/qq/other
			"city": "",
			"adcode": -1,
			"languages": "",
			"province": "",
			//省份，由ip地址解析
			"os": "Windows"
			//操作系统类型
		}]
	}
}
```

## **获取答题数据详情（单条查询）**

```cpp
//https://survey.imur.tencent.com/open/v1/answers/60ebdefe76051f6b8a37f782/613b1ea70bebcc94cec7f5bc?sign=132e7e09968c4dd43e3b4ede26f3584d&timestamp=1631266359
//示例请求

//sign生成（md5）appSecretiamsecretsid60ebdefe76051f6b8a37f782timestamp1631266359
//时间戳有时效性，demo失效了就更新时间戳重新计算sign

//仅返回有答案的题目
{
	"data": {
		"_id": "613b1ea70bebcc94cec7f5bc", 
    //答卷编号，aid
		"ip": "127.0.0.1",
		"client_id": "1226565806200979456",
		//浏览器编号
		"user_agent": "Mozilla\/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit\/537.36 (KHTML, like Gecko) Chrome\/92.0.4515.159 Safari\/537.36",
		//设备信息
		"started_at": 1631264344,
		//开始答题时间
		"ended_at": 1631264423,
		//结束答题时间
		"answer_consumed": 79,
		//答题时长：秒
		"answers": [{
			//答案列表
			"id": "ZWF2",
			//题目id
			"type": "radio",
			//题型
			"options": [{
				//选项
				"id": "AFA5",
				//选项id
				"text": "<p>社交观光团——注重与朋友的互动交流，享受在对局中自由探索，一路打闹一路躺赢<\/p>"
				//选项内容
			}]
		}, {
			"id": "KYJ6",
			"type": "radio",
			"options": [{
				"id": "EYW8",
				"text": "<p>2-比较不满意<\/p>"
			}]
		}, {
			"id": "IJDc",
			"type": "radio",
			"options": [{
				"id": "HVAe",
				"text": "<p>2-比较不满意<\/p>"
			}]
		}, {
			"id": "DJDl",
			"type": "select",
			"options": [{
				"id": "VPTs",
				"text": "18"
			}]
		}, {
			"id": "WY1i",
			"type": "checkbox",
			"options": [{
				"id": "HG1m",
				"text": "<p>手机游戏（含平板电脑）<\/p>"
			}, {
				"id": "RN1l",
				"text": "<p>网页游戏<\/p>"
			}]
		}, {
			"id": "AB1q",
			"type": "checkbox",
			"options": [{
				"id": "NG1t",
				"text": "<p>棋牌类游戏（如 QQ游戏大厅、联众游戏平台、JJ比赛等平台上的棋牌游戏）<\/p>"
			}, {
				"id": "YX1r",
				"text": "<p>大型客户端游戏（需要安装客户端，上网登录才能玩的大型客户端游戏，如 英雄联盟LOL、魔兽世界、穿越火线、守望先锋、梦幻西游、地下城与勇士、绝地求生、QQ炫舞等）<\/p>"
			}]
		}, {
			"id": "QJ1x",
			"type": "checkbox",
			"options": [{
				"id": "WK21",
				"text": "<p>【画面音乐】高质量的感官体验（如精致好看的画面\/画风、好听的音乐\/音效等）<\/p>"
			}, {
				"id": "WD20",
				"text": "<p>【策略思考】需要思考和策略能力的玩法<\/p>"
			}]
		}, {
			"id": "NO2e",
			"type": "checkbox",
			"options": [{
				"id": "HZ2l",
				"text": "<p>B--变形金刚<\/p>"
			}, {
				"id": "VR2k",
				"text": "<p>B--崩坏3（PC端）<\/p>"
			}, {
				"id": "OC2j",
				"text": "<p>B--堡垒之夜<\/p>"
			}]
		}, {
			"id": "YH44",
			"type": "checkbox",
			"options": [{
				"id": "OY4e",
				"text": "<p>视频网站：B站、腾讯视频、爱奇艺等<\/p>"
			}, {
				"id": "GI4c",
				"text": "<p>微信订阅号\/公众号\/视频号：游戏公众号或视频号等<\/p>"
			}, {
				"id": "WI4b",
				"text": "<p>应用商店中的游戏内容版块：TAPTAP、应用宝等<\/p>"
			}, {
				"id": "GU49",
				"text": "<p>社交网站：微博、小红书、QQ好友动态、兴趣部落、游戏圈子等<\/p>"
			}, {
				"id": "YP48",
				"text": "<p>大型论坛贴吧中的游戏吧或版块：百度贴吧、豆瓣、知乎等<\/p>"
			}, {
				"id": "WC4k",
				"text": "<p>王者荣耀手机端端官方网站<img src=\"https:\/\/mur-survey-1255655535.file.myqcloud.com\/static_files\/images\/5Lw7H8bhX5kAsdMGF6dsv5NLgmJEfN6HflSsHTpU.png?imageMogr2\/thumbnail\/512x&amp;width=512&amp;height=724\"><\/p>"
			}, {
				"id": "HI4j",
				"text": "<p>王者荣耀电脑端官方网站<img src=\"https:\/\/mur-survey-1255655535.file.myqcloud.com\/static_files\/images\/e64q3WclxWyXmjwZagn2CKTrcOCFlySFDVaXmMg9.png?imageMogr2\/thumbnail\/512x&amp;width=512&amp;height=724\"><\/p>"
			}]
		}, {
			"id": "PA4p",
			"type": "subjective",
			"text": "开放题"
		}, {
			"id": "SG4t",
			"type": "range",
			"value": 3
		}, {
			"id": "UQ86",
			"type": "range",
			"value": 5
		}, {
			"id": "LJ4w",
			"type": "matrixRadio",
			"groups": {
				"OM53": [{
					"id": "AG4y",
					"text": "<p>2-比较不满意<\/p>"
				}],
				"VT54": [{
					"id": "JQ4z",
					"text": "<p>3-一般<\/p>"
				}],
				"MC55": [{
					"id": "ON50",
					"text": "<p>4-比较满意<\/p>"
				}],
				"KI58": [{
					"id": "ON50",
					"text": "<p>4-比较满意<\/p>"
				}],
				"BO5a": [{
					"id": "ON50",
					"text": "<p>4-比较满意<\/p>"
				}],
				"WK56": [{
					"id": "ON50",
					"text": "<p>4-比较满意<\/p>"
				}],
				"SP57": [{
					"text": "<p>4-比较满意<\/p>",
					"id": "ON50"
				}],
				"KC59": [{
					"text": "<p>4-比较满意<\/p>",
					"id": "ON50"
				}],
				"SJ5b": [{
					"id": "ON50",
					"text": "<p>4-比较满意<\/p>"
				}]
			}
		}, {
			"id": "VU5c",
			"type": "matrixRadio",
			"groups": {
				"ZM5g": [{
					"id": "BN5e",
					"text": "<p>偶尔会玩一下<\/p>"
				}],
				"PV5h": [{
					"text": "<p>偶尔会玩一下<\/p>",
					"id": "BN5e"
				}]
			}
		}, {
			"id": "UF5i",
			"type": "matrixRadio",
			"groups": {
				"HB5t": [{
					"id": "LH5n",
					"text": "<p>非常满意<\/p>"
				}],
				"QK5q": [{
					"id": "ZX5m",
					"text": "<p>比较满意<\/p>"
				}],
				"BZ5r": [{
					"id": "LH5n",
					"text": "<p>非常满意<\/p>"
				}],
				"KP5s": [{
					"id": "LH5n",
					"text": "<p>非常满意<\/p>"
				}]
			}
		}, {
			"id": "ZS5w",
			"type": "matrixCheckbox",
			"groups": {
				"SO68": [{
					"id": "AD60",
					"text": "<p>是喜欢的选手\/大神\/创作者发的内容<\/p>"
				}, {
					"id": "UV61",
					"text": "<p>是喜欢的英雄相关的内容<\/p>"
				}],
				"HI69": [{
					"id": "PW5z",
					"text": "<p>内容质量高（有创意、操作优秀、讲解清晰等）<\/p>"
				}],
				"NP6a": [{
					"text": "<p>是喜欢的选手\/大神\/创作者发的内容<\/p>",
					"id": "AD60"
				}],
				"WJ6b": [{
					"id": "AD60",
					"text": "<p>是喜欢的选手\/大神\/创作者发的内容<\/p>"
				}],
				"ZV6d": [{
					"id": "AD60",
					"text": "<p>是喜欢的选手\/大神\/创作者发的内容<\/p>"
				}],
				"NZ6h": [{
					"id": "BU64",
					"text": "<p>作品\/意见征集活动<\/p>"
				}],
				"AK6e": [{
					"id": "UV61",
					"text": "<p>是喜欢的英雄相关的内容<\/p>"
				}],
				"XF6c": [{
					"id": "AD60",
					"text": "<p>是喜欢的选手\/大神\/创作者发的内容<\/p>"
				}],
				"PJ6f": [{
					"text": "<p>是喜欢的英雄相关的内容<\/p>",
					"id": "UV61"
				}],
				"HG6g": [{
					"text": "<p>可以得到福利奖励<\/p>",
					"id": "GP63"
				}]
			}
		}, {
			"id": "EG7m",
			"type": "cascade",
			"options": [{
				"id": "130000",
				"name": "河北省"
			}, {
				"id": "130400",
				"name": "邯郸市"
			}, {
				"id": "130408",
				"name": "永年区"
			}],
			"subTitles": [{
				"id": "ZR87",
				"text": "省"
			}, {
				"id": "ZY88",
				"text": "市"
			}, {
				"id": "DM89",
				"text": "区"
			}]
		}, {
			"id": "RG7t",
			"type": "matrixRange",
			"groups": {
				"XD7u": 2,
				"LG7v": 6,
				"UM7w": 5,
				"UG7x": 4
			}
		}, {
			"id": "XR8d",
			"type": "matrixRange",
			"groups": {
				"XD7u": 3
			}
		}, {
			"id": "VJ80",
			"type": "attachment",
			"options": [{
				"text": "https:\/\/mur-private-assets-1255655535.file.myqcloud.com\/survey\/de088ede01fe58ddd43f815bb7f7af21_1631264416.jpg"
			}, {
				"text": "https:\/\/mur-private-assets-1255655535.file.myqcloud.com\/survey\/76aa2f08123cce11cb31bc67b1b31550_1631264416.jpg"
			}, {
				"text": "https:\/\/mur-private-assets-1255655535.file.myqcloud.com\/survey\/1a24dd14fa93921a27343dee523b0150_1631264416.png"
			}]
		}, {
			"id": "UND2",
			"type": "sort",
			"groups": {
				"VXK5": 2,
				"NRY8": 3,
				"TTU7": 4,
				"NLL3": 5,
				"FVF4": 6,
				"SHX6": 1
			}
		}],
		"abnormal_end": false,
		//是否非正常结束
		"answer_finished": true,
		//答题状态，true=已完成，false=未完成
		"user_type": "weak_third_party",
		//用户ID类型
		"uid": "testid",
		//用户ID
		"uid_info": "testinfo",
		//自定义内容
		"channel": "-",
		//来源平台
		"created_at": "2021-09-10 17:00:23",
		"updated_at": "2021-09-10 17:00:23",
		"device": "other",
		"nation": "",
		//国家或地区
		"browser": "Chrome",
		//浏览器类型
		"source": "other",
		//用户ID渠道，wx/qq/other
		"city": "",
		"adcode": -1,
		"languages": "",
		"province": "",
		//省份，由ip地址解析
		"os": "Windows"
		//操作系统类型
	}
}
```

## 题型（type）有效值说明

| type           | 题型    |
| -------------- | ----- |
| radio          | 单选题   |
| checkbox       | 多选题   |
| select         | 下拉题   |
| subjective     | 主观题   |
| range          | 量表题   |
| matrixRadio    | 矩阵单选题 |
| matrixCheckbox | 矩阵多选题 |
| matrixRange    | 矩阵量表题 |
| cascade        | 联动题   |
| attachment     | 附件上传题 |
| sort           | 排序题   |

