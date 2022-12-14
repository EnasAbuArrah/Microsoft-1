# K-Means èç±»

[![Andrew Ng explains Clustering](https://img.youtube.com/vi/hDmNF9JG3lo/0.jpg)](https://youtu.be/hDmNF9JG3lo "Andrew Ng explains Clustering")

> ð¥ åå»ä¸å¾è§çè§é¢ï¼Andrew Ng è§£éèç±»

## [è¯¾åæµéª](https://gray-sand-07a10f403.1.azurestaticapps.net/quiz/29/)

å¨æ¬è¯¾ä¸­ï¼æ¨å°å­¦ä¹ å¦ä½ä½¿ç¨ Scikit-learn åæ¨ä¹åå¯¼å¥çå°¼æ¥å©äºé³ä¹æ°æ®éåå»ºèç±»ãæä»¬å°ä»ç» K-Means èç±» çåºç¡ç¥è¯ãè¯·è®°ä½ï¼æ­£å¦æ¨å¨ä¸ä¸è¯¾ä¸­å­¦å°çï¼ä½¿ç¨èç±»çæ¹æ³æå¾å¤ç§ï¼æ¨ä½¿ç¨çæ¹æ³åå³äºæ¨çæ°æ®ãæä»¬å°å°è¯ K-Meansï¼å ä¸ºå®æ¯æå¸¸è§çèç±»ææ¯ãè®©æä»¬å¼å§å§ï¼

æ¨å°äºè§£çæ¯è¯­ï¼

- è½®å»æå
- æèæ¹æ³
- æ¯æ§
- æ¹å·®

## ä»ç»

[K-Means Clustering](https://wikipedia.org/wiki/K-means_clustering) æ¯ä¸ç§æºèªä¿¡å·å¤çé¢åçæ¹æ³ãå®ç¨äºä½¿ç¨ä¸ç³»åè§å¯å°æ°æ®ç»åååååä¸ºâkâä¸ªèç±»ãæ¯ä¸ªè§å¯é½ç¨äºå¯¹ææ¥è¿å¶æè¿âå¹³åå¼âæèç±»ä¸­å¿ç¹çç»å®æ°æ®ç¹è¿è¡åç»ã

èç±»å¯ä»¥å¯è§åä¸º [Voronoi å¾](https://wikipedia.org/wiki/Voronoi_diagram)ï¼å¶ä¸­åæ¬ä¸ä¸ªç¹ï¼æâç§å­âï¼åå¶ç¸åºçåºåã

![voronoi diagram](../images/voronoi.png)

> [Jen Looper](https://twitter.com/jenlooper)ä½å¾

K-Means èç±»è¿ç¨[åä¸æ­¥æ§è¡](https://scikit-learn.org/stable/modules/clustering.html#k-means)ï¼

1. è¯¥ç®æ³éè¿ä»æ°æ®éä¸­éæ ·æ¥éæ© k ä¸ªä¸­å¿ç¹ãå¨æ­¤ä¹åï¼å®å¾ªç¯ï¼
   1. å®å°æ¯ä¸ªæ ·æ¬åéå°æè¿çè´¨å¿ã
   2. å®éè¿ååéç»ååè´¨å¿çæææ ·æ¬çå¹³åå¼æ¥åå»ºæ°è´¨å¿ã
   3. ç¶åï¼å®è®¡ç®æ°æ§è´¨å¿ä¹é´çå·®å¼å¹¶éå¤ç´å°è´¨å¿ç¨³å®ã

ä½¿ç¨ K-Means çä¸ä¸ªç¼ºç¹åæ¬æ¨éè¦å»ºç«âkâï¼å³è´¨å¿çæ°éãå¹¸è¿çæ¯ï¼âèé¨æ³åâæå©äºä¼°è®¡âkâçè¯å¥½èµ·å§å¼ãè¯ä¸ä¸å§ã

## åç½®æ¡ä»¶

æ¨å°ä½¿ç¨æ¬è¯¾ç *notebook.ipynb* æä»¶ï¼å¶ä¸­åå«æ¨å¨ä¸ä¸è¯¾ä¸­æåçæ°æ®å¯¼å¥ååæ­¥æ¸çã

## ç»ä¹  - åå¤

é¦ååççæ­æ²æ°æ®ã

1. åå»ºä¸ä¸ªç®±çº¿å¾ï¼`boxplot()` ä¸ºæ¯ä¸åè°ç¨ï¼

    ```python
    plt.figure(figsize=(20,20), dpi=200)
    
    plt.subplot(4,3,1)
    sns.boxplot(x = 'popularity', data = df)
    
    plt.subplot(4,3,2)
    sns.boxplot(x = 'acousticness', data = df)
    
    plt.subplot(4,3,3)
    sns.boxplot(x = 'energy', data = df)
    
    plt.subplot(4,3,4)
    sns.boxplot(x = 'instrumentalness', data = df)
    
    plt.subplot(4,3,5)
    sns.boxplot(x = 'liveness', data = df)
    
    plt.subplot(4,3,6)
    sns.boxplot(x = 'loudness', data = df)
    
    plt.subplot(4,3,7)
    sns.boxplot(x = 'speechiness', data = df)
    
    plt.subplot(4,3,8)
    sns.boxplot(x = 'tempo', data = df)
    
    plt.subplot(4,3,9)
    sns.boxplot(x = 'time_signature', data = df)
    
    plt.subplot(4,3,10)
    sns.boxplot(x = 'danceability', data = df)
    
    plt.subplot(4,3,11)
    sns.boxplot(x = 'length', data = df)
    
    plt.subplot(4,3,12)
    sns.boxplot(x = 'release_date', data = df)
    ```

    è¿ä¸ªæ°æ®æç¹åæï¼éè¿è§å¯æ¯ä¸åä½ä¸ºç®±çº¿å¾ï¼ä½ å¯ä»¥çå°å¼å¸¸å¼ã

    ![outliers](../images/boxplots.png)

æ¨å¯ä»¥æµè§æ°æ®éå¹¶å é¤è¿äºå¼å¸¸å¼ï¼ä½è¿ä¼ä½¿æ°æ®éå¸¸å°ã

1. ç°å¨ï¼éæ©æ¨å°ç¨äºèç±»ç»ä¹ çåãéæ©å·æç¸ä¼¼èå´çé£äºå¹¶å° `artist_top_genre` åç¼ç ä¸ºæ°å­ç±»åçæ°æ®ï¼

    ```python
    from sklearn.preprocessing import LabelEncoder
    le = LabelEncoder()
    
    X = df.loc[:, ('artist_top_genre','popularity','danceability','acousticness','loudness','energy')]
    
    y = df['artist_top_genre']
    
    X['artist_top_genre'] = le.fit_transform(X['artist_top_genre'])
    
    y = le.transform(y)
    ```

1. ç°å¨æ¨éè¦éæ©è¦å®ä½çèç±»æ°éãæ¨ç¥éæä»¬ä»æ°æ®éä¸­ææåº 3 ç§æ­æ²æµæ´¾ï¼æä»¥è®©æä»¬å°è¯ 3 ç§ï¼

    ```python
    from sklearn.cluster import KMeans
    
    nclusters = 3 
    seed = 0
    
    km = KMeans(n_clusters=nclusters, random_state=seed)
    km.fit(X)
    
    # Predict the cluster for each data point
    
    y_cluster_kmeans = km.predict(X)
    y_cluster_kmeans
    ```

æ¨ä¼çå°æå°åºçæ°ç»ï¼å¶ä¸­åå«æ°æ®å¸§æ¯ä¸è¡çé¢æµèç±»ï¼0ã1 æ 2ï¼ã

1. ä½¿ç¨æ­¤æ°ç»è®¡ç®âè½®å»åæ°âï¼

    ```python
    from sklearn import metrics
    score = metrics.silhouette_score(X, y_cluster_kmeans)
    score
    ```

## è½®å»åæ°

å¯»æ¾æ¥è¿ 1 çè½®å»åæ°ãè¯¥åæ°ä» -1 å° 1 ä¸ç­ï¼å¦æåæ°ä¸º 1ï¼åè¯¥èç±»å¯éä¸ä¸å¶ä»èç±»åç¦»è¯å¥½ãæ¥è¿ 0 çå¼è¡¨ç¤ºéå èç±»ï¼æ ·æ¬éå¸¸æ¥è¿ç¸é»èç±»çå³ç­è¾¹çã[æ¥æº](https://dzone.com/articles/kmeans-silhouette-score-explained-with-python-exam)ã

æä»¬çåæ°æ¯ **0.53**ï¼æä»¥æ­£å¥½å¨ä¸­é´ãè¿è¡¨ææä»¬çæ°æ®ä¸æ¯ç¹å«éåè¿ç§ç±»åçèç±»ï¼ä½è®©æä»¬ç»§ç»­ã

### ç»ä¹  - å»ºç«æ¨¡å

1. å¯¼å¥ `KMeans` å¹¶å¯å¨èç±»è¿ç¨ã

    ```python
    from sklearn.cluster import KMeans
    wcss = []
    
    for i in range(1, 11):
        kmeans = KMeans(n_clusters = i, init = 'k-means++', random_state = 42)
        kmeans.fit(X)
        wcss.append(kmeans.inertia_)
    
    ```

    è¿éæå ä¸ªé¨åéè¦è§£éã

    > ð rangeï¼è¿äºæ¯èç±»è¿ç¨çè¿­ä»£

    > ð random_stateï¼âç¡®å®è´¨å¿åå§åçéæºæ°çæãâ [æ¥æº](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html#sklearn.cluster.KMeans)

    > ð WCSSï¼âèç±»åå¹³æ¹åâæµéèç±»åææç¹å°èç±»è´¨å¿çå¹³æ¹å¹³åè·ç¦»ã[æ¥æº](https://medium.com/@ODSC/unsupervised-learning-evaluating-clusters-bd47eed175ce)ã

    > ð Inertiaï¼K-Means ç®æ³å°è¯éæ©è´¨å¿ä»¥æå°åâæ¯æ§âï¼âæ¯æ§æ¯è¡¡éåé¨ç¸å¹²ç¨åº¦çä¸ç§æ¹æ³âã[æ¥æº](https://scikit-learn.org/stable/modules/clustering.html)ãè¯¥å¼å¨æ¯æ¬¡è¿­ä»£æ¶éå å° wcss åéã

    > ð k-means++ï¼å¨ [Scikit-learn ä¸­ï¼](https://scikit-learn.org/stable/modules/clustering.html#k-means)æ¨å¯ä»¥ä½¿ç¨âk-means++âä¼åï¼å®âå°è´¨å¿åå§åä¸ºï¼éå¸¸ï¼å½¼æ­¤è¿ç¦»ï¼å¯¼è´å¯è½æ¯éæºåå§åæ´å¥½çç»æã

### æèæ¹æ³

ä¹åï¼æ¨æ¨æµï¼å ä¸ºæ¨å·²ç»å®ä½äº 3 ä¸ªæ­æ² genreï¼æä»¥æ¨åºè¯¥éæ© 3 ä¸ªèç±»ãä½ççæ¯è¿æ ·åï¼

1. ä½¿ç¨æèæ¹æ³æ¥ç¡®è®¤ã

    ```python
    plt.figure(figsize=(10,5))
    sns.lineplot(range(1, 11), wcss,marker='o',color='red')
    plt.title('Elbow')
    plt.xlabel('Number of clusters')
    plt.ylabel('WCSS')
    plt.show()
    ```

    ä½¿ç¨ `wcss` æ¨å¨ä¸ä¸æ­¥ä¸­æå»ºçåéåå»ºä¸ä¸ªå¾è¡¨ï¼æ¾ç¤ºèé¨âå¼¯æ²âçä½ç½®ï¼è¿è¡¨ç¤ºæä½³èç±»æ°ãä¹è®¸**æ¯** 3ï¼

    ![elbow method](../images/elbow.png)

## ç»ä¹  - æ¾ç¤ºèç±»

1. åæ¬¡å°è¯è¯¥è¿ç¨ï¼è¿æ¬¡è®¾ç½®ä¸ä¸ªèç±»ï¼å¹¶å°èç±»æ¾ç¤ºä¸ºæ£ç¹å¾ï¼

    ```python
    from sklearn.cluster import KMeans
    kmeans = KMeans(n_clusters = 3)
    kmeans.fit(X)
    labels = kmeans.predict(X)
    plt.scatter(df['popularity'],df['danceability'],c = labels)
    plt.xlabel('popularity')
    plt.ylabel('danceability')
    plt.show()
    ```

1. æ£æ¥æ¨¡åçåç¡®æ§ï¼

    ```python
    labels = kmeans.labels_
    
    correct_labels = sum(y == labels)
    
    print("Result: %d out of %d samples were correctly labeled." % (correct_labels, y.size))
    
    print('Accuracy score: {0:0.2f}'. format(correct_labels/float(y.size)))
    ```

    è¿ä¸ªæ¨¡åçåç¡®æ§ä¸æ¯å¾å¥½ï¼èç±»çå½¢ç¶ç»äºä½ ä¸ä¸ªæç¤ºã

    ![clusters](../images/clusters.png)

    è¿äºæ°æ®å¤ªä¸å¹³è¡¡ï¼ç¸å³æ§å¤ªä½ï¼åå¼ä¹é´çå·®å¼å¤ªå¤§ï¼æ æ³å¾å¥½å°èç±»ãäºå®ä¸ï¼å½¢æçèç±»å¯è½åå°æä»¬ä¸é¢å®ä¹çä¸ä¸ªç±»åç±»å«çä¸¥éå½±åææ­æ²ãé£æ¯ä¸ä¸ªå­¦ä¹ çè¿ç¨ï¼

    å¨ Scikit-learn çææ¡£ä¸­ï¼ä½ å¯ä»¥çå°åè¿æ ·çæ¨¡åï¼èç±»ååä¸æ¯å¾å¥½ï¼æä¸ä¸ªâæ¹å·®âé®é¢ï¼

    ![problem models](../images/problems.png)
    
    > å¾æ¥èª Scikit-learn

## æ¹å·®

> æ¹å·®è¢«å®ä¹ä¸ºâæ¥èªåå¼çå¹³æ¹å·®çå¹³åå¼â[æº](https://www.mathsisfun.com/data/standard-deviation.html)ãå¨è¿ä¸ªèç±»é®é¢çä¸ä¸æä¸­ï¼å®æçæ¯æä»¬æ°æ®éçæ°éå¾å¾ä¸å¹³åå¼ç¸å·®å¤ªå¤çæ°æ®ã
>
> âè¿æ¯èèå¯ä»¥çº æ­£æ­¤é®é¢çæææ¹æ³çå¥½æ¶æºãç¨å¾®è°æ´ä¸ä¸æ°æ®ï¼ä½¿ç¨ä¸åçåï¼ä½¿ç¨ä¸åçç®æ³ï¼æç¤ºï¼å°è¯[ç¼©æ¾æ°æ®](https://www.mygreatlearning.com/blog/learning-data-science-with-k-means-clustering/)ä»¥å¯¹å¶è¿è¡æ ååå¹¶æµè¯å¶ä»åã
>
> > è¯è¯è¿ä¸ªâ[æ¹å·®è®¡ç®å¨](https://www.calculatorsoup.com/calculators/statistics/variance-calculator.php)âæ¥æ´å¤å°çè§£è¿ä¸ªæ¦å¿µã

---

## ðææ

è±ä¸äºæ¶é´å¨è¿ä¸ªç¬è®°æ¬ä¸ï¼è°æ´åæ°ãæ¨è½å¦éè¿æ´å¤å°æ¸çæ°æ®ï¼ä¾å¦ï¼å»é¤å¼å¸¸å¼ï¼æ¥æé«æ¨¡åçåç¡®æ§ï¼æ¨å¯ä»¥ä½¿ç¨æéä¸ºç»å®çæ°æ®æ ·æ¬èµäºæ´å¤æéãä½ è¿è½åäºä»ä¹æ¥åå»ºæ´å¥½çèç±»ï¼

æç¤ºï¼å°è¯ç¼©æ¾æ¨çæ°æ®ãç¬è®°æ¬ä¸­çæ³¨éä»£ç æ·»å äºæ åç¼©æ¾ï¼ä½¿æ°æ®åå¨èå´æ¹é¢æ´å ç¸ä¼¼ãæ¨ä¼åç°ï¼å½è½®å»åæ°ä¸éæ¶ï¼èé¨å¾ä¸­çâæ­ç»âåå¾å¹³æ»ãè¿æ¯å ä¸ºä¸ç¼©æ¾æ°æ®å¯ä»¥è®©æ¹å·®è¾å°çæ°æ®æ¿è½½æ´å¤çæéãå¨[è¿é](https://stats.stackexchange.com/questions/21222/are-mean-normalization-and-feature-scaling-needed-for-k-means-clustering/21226#21226)éè¯»æ´å¤å³äºè¿ä¸ªé®é¢ç[ä¿¡æ¯](https://stats.stackexchange.com/questions/21222/are-mean-normalization-and-feature-scaling-needed-for-k-means-clustering/21226#21226)ã

## [è¯¾åæµéª](https://gray-sand-07a10f403.1.azurestaticapps.net/quiz/30/)

## å¤ä¹ ä¸èªå­¦

çç[åè¿æ ·](https://user.ceng.metu.edu.tr/~akifakkus/courses/ceng574/k-means/)ç K-Means æ¨¡æå¨ãæ¨å¯ä»¥ä½¿ç¨æ­¤å·¥å·æ¥å¯è§åæ ·æ¬æ°æ®ç¹å¹¶ç¡®å®å¶è´¨å¿ãæ¨å¯ä»¥ç¼è¾æ°æ®çéæºæ§ãèç±»æ°åè´¨å¿æ°ãè¿æ¯å¦æå©äºæ¨äºè§£å¦ä½å¯¹æ°æ®è¿è¡åç»ï¼

å¦å¤ï¼ççæ¯å¦ç¦å¤§å­¦ç [K-Means è®²ä¹](https://stanford.edu/~cpiech/cs221/handouts/kmeans.html)ã

## ä½ä¸

[å°è¯ä¸åçèç±»æ¹æ³](./assignment.zh-cn.md)

