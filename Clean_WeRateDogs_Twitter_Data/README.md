# 清洗 WeRateDogs 推特数据

## 收集数据<br>
1、读取CSV文件到数据框中<br>
2、从网页收集推特图像的预测数据<br>
3、使用 Tweepy 来查询推特 API，收集数据<br>

## 评估数据<br>
1、使用目测评估数据集<br>
2、使用编程评估数据集<br>  

df_twitter数据集<br>  

  source 含有格式字符<br>
  name 列内容提取不正确<br>
  tweet_id数据类型是int，不正确<br>
  timestamp时间格式错误<br>
  in_reply_to_status_id、in_reply_to_user_id、retweeted_status_id、retweeted_status_user_id、retweeted_status_timestamp 为转发的信息
  评分列rating_numerator/rating_denominator 部分内容提取错误<br>
  expanded_urls 列内容有缺失<br>
  含有没有图片的推文条目，我们只需要含有图片的原始评级 (不包括转发)<br>  
  
df_image数据集<br>  
 
tweet_id数据类型是int，不正确<br>
p1\p2\p3 名字大小写不一致<br>  

df_tweet数据集<br>  

tweet_id数据类型是int，不正确<br>  

清洁度<br>   

“地位”（即 doggo、floofer、pupper 和 puppo）分开在四列中<br> 
df_twitter\df_image\df_tweet 不在一个数据集中<br> 

## 清理数据
source 含有格式字符：使用正则表达式提取正确的内容，并删除格式字符<br> 
name 列内容提取不正确：名字是小写字母的，对其进行重新提取text列内容中含"name is "\"named"后面的名字，对于没有名字的替换成"No_name"。None的替换成"No_name"<br> 
df_twitter数据集、df_image数据集、df_tweet数据集 tweet_id数据类型是int，不正确：weet_id列应该是object类型，用astype() 把int改成object。<br> 
timestamp时间格式错误:使用to_datetime 更改timestamp时间格式<br>
n_reply_to_status_id、in_reply_to_user_id、retweeted_status_id、retweeted_status_user_id、retweeted_status_timestamp 为转发的信息:in_reply_to_status_id、in_reply_to_user_id、retweeted_status_id、retweeted_status_user_id、retweeted_status_timestamp 为转发的信息，这几列为non-null的所有条目删除（选出这几列为空值的行）。都为空值了，移除掉这几列。<br> 
评分列rating_numerator/rating_denominator 部分内容提取错误:查找评分通常不以 10 作为分母的数据，将其与text进行比较，修改为正确的评分。<br> 
expanded_urls 列内容有缺失:使用dropna，删除内容有缺失的行。<br> 
p1\p2\p3 名字大小写不一致:使用str.lower() 把p1\p2\p3名字改成全小写。<br> 
“地位”（即 doggo、floofer、pupper 和 puppo）分开在四列中:创建stage列合并四列内容，将分开的四列内容删除<br> 
df_twitter\df_image\df_tweet 不在一个数据集中:使用pd.merge函数，how='inner'(可以删掉没有图片的推文条目)，将df_image_clean\df_tweet_clean\df_twitter_clean合并到新数据集中<br> 


## 存储数据
## 数据分析
对狗狗不同地位的情况，转发数以及喜爱数进行探究。<br> 
对狗狗的地位分析其转发数的情况。<br> 

## 结论
1、不同狗狗地位中，pupper所占的数量最多，估计推特上以此种地位的狗狗居多。<br> 
2、不同狗狗地位中，puppo\doggo地位的狗狗转发数的平均值最高，puppo 地位的狗狗喜爱数的平均值最高，由此可知puppo 地位的狗狗大家更喜欢。<br> 
3、由以上数据得出，不同地位的狗狗转发数与狗狗喜爱数是有一定的关系的。<br> 
