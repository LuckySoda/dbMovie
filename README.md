# dbMovie
由于豆瓣api屏蔽了微信小程序，需要使用nginx代理请求豆瓣API的数据，以下是nginx的配置
location  / {  
  proxy_store off;
  proxy_redirect off;
  proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  proxy_set_header X-Real-IP $remote_addr;
  proxy_set_header Referer 'no-referrer-when-downgrade';
  proxy_set_header User-Agent 'Mozilla/5.0 (Windows NT 10.0;WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/62.0.3202.94     Safari/537.36';
  proxy_connect_timeout 600;
  proxy_read_timeout 600;
  proxy_send_timeout 600;
  proxy_pass https://api.douban.com;
}
