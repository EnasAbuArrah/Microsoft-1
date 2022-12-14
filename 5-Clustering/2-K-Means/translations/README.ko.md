# K-Means clustering

[![Andrew Ng explains Clustering](https://img.youtube.com/vi/hDmNF9JG3lo/0.jpg)](https://youtu.be/hDmNF9JG3lo "Andrew Ng explains Clustering")

> ๐ฅ ์์์ ๋ณด๋ ค๋ฉด ์ด๋ฏธ์ง ํด๋ฆญ: Andrew Ng explains clustering

## [๊ฐ์ ์  ํด์ฆ](https://gray-sand-07a10f403.1.azurestaticapps.net/quiz/29/)

์ด ๊ฐ์์์, Scikit-learn๊ณผ ํจ๊ป ์ด์ ์ ๊ฐ์ ธ์จ ๋์ด์ง๋ฆฌ์ ์์ ๋ฐ์ดํฐ์์ผ๋ก ํด๋ฌ์คํฐ ์ ์ ๋ฐฉ์์ ๋ฐฐ์ธ ์์ ์๋๋ค. Clustering์ ์ํ K-Means ๊ธฐ์ด๋ฅผ ๋ค๋ฃจ๊ฒ ๋ฉ๋๋ค. ์ฐธ๊ณ ๋ก, ์ด์  ๊ฐ์์์ ๋ฐฐ์ ๋๋๋ก, ํด๋ฌ์คํฐ๋ก ์์ํ๋ ์ฌ๋ฌ ๋ฐฉ์์ด ์๊ณ  ๋ฐ์ดํฐ๋ฅผ ๊ธฐ๋ฐํ ๋ฐฉ์๋ ์์ต๋๋ค. ๊ฐ์ฅ ์ผ๋ฐ์  clustering ๊ธฐ์ ์ธ K-Means์ ์๋ํด๋ณด๋ ค๊ณ  ํฉ๋๋ค. ์์ํด๋ด๋๋ค!

๋ค์ ์ฉ์ด๋ฅผ ๋ฐฐ์ฐ๊ฒ ๋ฉ๋๋ค:

- Silhouette scoring
- Elbow method
- Inertia
- Variance

## ์๊ฐ

[K-Means Clustering](https://wikipedia.org/wiki/K-means_clustering)์ ์ ํธ ์ฒ๋ฆฌ ๋๋ฉ์ธ์์ ํ์๋ ๋ฐฉ์์๋๋ค. observations ๊ณ์ด๋ก์ ๋ฐ์ดํฐ ๊ทธ๋ฃน์ 'k' ํด๋ฌ์คํฐ๋ก ๋๋๊ณ  ๋ถํ ํ๋ฉฐ ์ฌ์ฉํ์ต๋๋ค. ๊ฐ์ observation์ ๊ฐ๊น์ด 'mean', ๋๋ ํด๋ฌ์คํฐ์ ์ค์ฌ ํฌ์ธํธ์ ์ฃผ์ด์ง ์ ๋ฐํ ๋ฐ์ดํฐ ํฌ์ธํธ๋ฅผ ๊ทธ๋ฃน์ผ๋ก ๋ฌถ๊ธฐ ์ํด์ ์๋ํฉ๋๋ค.

ํด๋ฌ์คํฐ๋ ํฌ์ธํธ(๋๋ 'seed')์ ์ผ์นํ๋ ์์ญ์ ํฌํจํ, [Voronoi diagrams](https://wikipedia.org/wiki/Voronoi_diagram)์ผ๋ก ์๊ฐํํ  ์ ์์ต๋๋ค.

![voronoi diagram](../images/voronoi.png)

> infographic by [Jen Looper](https://twitter.com/jenlooper)

K-Means clustering์ [executes in a three-step process](https://scikit-learn.org/stable/modules/clustering.html#k-means)๋ก ์ฒ๋ฆฌ๋ฉ๋๋ค:

1. ์๊ณ ๋ฆฌ์ฆ์ ๋ฐ์ดํฐ์์์ ์ํ๋งํ ์ค์ฌ ํฌ์ธํธ์ k-number๋ฅผ ์ ํํฉ๋๋ค. ๋ฐ๋ณตํฉ๋๋ค:
    1. ๊ฐ์ฅ ๊ฐ๊น์ด ๋ฌด๊ฒ ์ค์ฌ์ ๊ฐ์ ์ํ์ ํ ๋นํฉ๋๋ค.
    2. ์ด์ ์ ๋ฌด๊ฒ ์ค์ฌ์์ ํ ๋น๋ ๋ชจ๋  ์ํ์ ํ๊ท  ๊ฐ์ ๊ฐ์ง๋ฉด์ ์๋ก์ด ๋ฌด๊ฒ ์ค์ฌ์ ๋ง๋ญ๋๋ค.
    3. ๊ทธ๋ฌ๋ฉด, ์๋กญ๊ณ  ์ค๋๋ ๋ฌด๊ฒ ์ค์ฌ ์ฌ์ด์ ๊ฑฐ๋ฆฌ๋ฅผ ๊ณ์ฐํ๊ณ  ๋ฌด๊ณ ์ค์ฌ์ด ์์ ๋  ๋๊น์ง ๋ฐ๋ณตํฉ๋๋ค.

K-Means์ ์ฌ์ฉํ ํ ๊ฐ์ง ์ฝ์ ์ ๋ฌด๊ฒ ์ค์ฌ์ ์ซ์๋ฅผ, 'k'๋ก ํด์ผ ๋๋ค๋ ์ฌ์ค์๋๋ค. ๋คํ์ค๋ฝ๊ฒ 'elbow method'๋ 'k' ๊ฐ์ ์ข๊ฒ ์์ํ  ์ ์๊ฒ ์ถ์ ํ๋ ๋ฐ ๋์์ ๋ฐ์ ์ ์์ต๋๋ค. ๋ช ๋ถ๋์ ์๋ํ  ์์ ์๋๋ค.

## ์ ์  ์กฐ๊ฑด

๋ง์ง๋ง ๊ฐ์์์ ํ๋ ๋ฐ์ดํฐ๋ฅผ ๊ฐ์ ธ์์ ๋ฏธ๋ฆฌ ์ ๋ฆฌํ ์ด ๊ฐ์์ _notebook.ipynb_ ํ์ผ๋ก ์์ํ  ์์ ์๋๋ค.

## ์ฐ์ต - ์ค๋นํ๊ธฐ

๋ธ๋ ๋ฐ์ดํฐ๋ฅผ ๋ค์ ๋ณด๋ ๊ฒ๋ถํฐ ์์ํฉ๋๋ค.

1. ๊ฐ ์ด์ `boxplot()`์ ๋ถ๋ฌ์, boxplot์ ๋ง๋ญ๋๋ค:

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

    ์ด ๋ฐ์ดํฐ๋ ์ฝ๊ฐ์ ๋ธ์ด์ฆ๊ฐ ์์ต๋๋ค: ๊ฐ ์ด์ boxplot์ผ๋ก ์ง์ผ๋ณด๋ฉด ์์๋ผ์ด์ด๋ฅผ ๋ณผ ์ ์์ต๋๋ค.

    ![outliers](../images/boxplots.png)

๋ฐ์ดํฐ์์ ์ฐพ๊ณ  ์ด ์์๋ผ์ด์ด๋ฅผ ์ ๊ฑฐํ๋ ๋์ ์, ๋ฐ์ดํฐ๋ ๊ฝค ์์์ง๊ฒ ๋ฉ๋๋ค.

1. ์ง๊ธ๋ถํฐ, clustering ์ฐ์ต์์ ์ฌ์ฉํ  ์ด์ ์ ํํฉ๋๋ค. ์ ์ฌํ ๋ฒ์๋ก ํ๋ ์ ํํ๊ณ  `artist_top_genre` ์ด์ ์ซ์ ๋ฐ์ดํฐ๋ก ์ธ์ฝ๋ฉํฉ๋๋ค:

    ```python
    from sklearn.preprocessing import LabelEncoder
    le = LabelEncoder()
    
    X = df.loc[:, ('artist_top_genre','popularity','danceability','acousticness','loudness','energy')]
    
    y = df['artist_top_genre']
    
    X['artist_top_genre'] = le.fit_transform(X['artist_top_genre'])
    
    y = le.transform(y)
    ```

1. ์ด์  ์ผ๋ง๋ ๋ง์ ํด๋ฌ์คํฐ๋ฅผ ํ๊ฒ์ผ๋ก ์ก์์ง ์ ํํด์ผ ํฉ๋๋ค. ๋ฐ์ดํฐ์์์ ์กฐ๊ฐ๋ธ 3๊ฐ ์ฅ๋ฅด๊ฐ ์์ผ๋ฏ๋ก, 3๊ฐ๋ฅผ ์๋ํฉ๋๋ค:

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

๋ฐ์ดํฐ ํ๋ ์์ ๊ฐ ์ด์์ ์์ธก๋ ํด๋ฌ์คํฐ (0, 1,๋๋ 2)๋ก ๋ฐฐ์ด์ ์ถ๋ ฅํด์ ๋ณผ ์ ์์ต๋๋ค.

1. ๋ฐฐ์ด๋ก 'silhouette score'๋ฅผ ๊ณ์ฐํฉ๋๋ค:

    ```python
    from sklearn import metrics
    score = metrics.silhouette_score(X, y_cluster_kmeans)
    score
    ```

## Silhouette score

1์ ๊ทผ์ ํ silhouette score๋ฅผ ์ฐพ์๋ด๋๋ค. ์ด ์ ์๋ -1์์ 1๊น์ง ๋ค์ํ๋ฉฐ, ํด๋ฌ์คํฐ๊ฐ ๋ฐ์ ํ์ฌ ๋ค๋ฅธ ๊ฒ๊ณผ ์-๋ถ๋ฆฌ๋ฉ๋๋ค. 0 ๊ทผ์  ๊ฐ์ ์ฃผ๋ณ ํด๋ฌ์คํฐ์ decision boundary์ ๋งค์ฐ ๊ฐ๊น์ด ์ํ๊ณผ ํจ๊ป ํด๋ฌ์คํฐ๋ฅผ ์ค๋ฒ๋ฉํค์ ๋ํ๋๋๋ค. [source](https://dzone.com/articles/kmeans-silhouette-score-explained-with-python-exam).

**.53** ์ ์ด๋ฏ๋ก, ์ค๊ฐ์ ์์นํฉ๋๋ค. ๋ฐ์ดํฐ๊ฐ ์ด clustering ํ์์ ํนํ ์-๋ง์ง ์๋ค๋ ์ ์ ๋ํ๋ด๊ณ  ์์ง๋ง, ๊ณ์ ์งํํฉ๋๋ค.

### ์ฐ์ต - ๋ชจ๋ธ ๋ง๋ค๊ธฐ

1. `KMeans`์ import ํ๊ณ  clustering ์ฒ๋ฆฌ๋ฅผ ์์ํฉ๋๋ค.

    ```python
    from sklearn.cluster import KMeans
    wcss = []
    
    for i in range(1, 11):
        kmeans = KMeans(n_clusters = i, init = 'k-means++', random_state = 42)
        kmeans.fit(X)
        wcss.append(kmeans.inertia_)
    
    ```

    ์ฌ๊ธฐ ์ค๋ช์ ๋ท๋ฐ์นจํ  ๋ช ํํธ๊ฐ ์์ต๋๋ค.

    > ๐ range: clustering ํ๋ก์ธ์ค์ ๋ฐ๋ณต์๋๋ค

    > ๐ random_state: "Determines random number generation for centroid initialization."[source](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html#sklearn.cluster.KMeans)

    > ๐ WCSS:  "within-cluster sums of squares"์ ํด๋ฌ์คํฐ ๋ฌด๊ฒ ์ค์ฌ์ผ๋ก ํด๋ฌ์คํฐ์์ ๋ชจ๋  ํฌ์ธํธ์ squared average ๊ฑฐ๋ฆฌ๋ฅผ ์ธก์ ํฉ๋๋ค. [source](https://medium.com/@ODSC/unsupervised-learning-evaluating-clusters-bd47eed175ce).
   
    > ๐ Inertia: K-Means ์๊ณ ๋ฆฌ์ฆ์ 'inertia'๋ฅผ ์ต์๋ก ์ ์งํ๊ธฐ ์ํด์ ๋ฌด๊ฒ ์ค์ฌ์ ์ ํํ๋ ค๊ณ  ์๋ํฉ๋๋ค, "a measure of how internally coherent clusters are."[source](https://scikit-learn.org/stable/modules/clustering.html). ๊ฐ์ ๊ฐ ๋ฐ๋ณต์์ wcss ๋ณ์๋ก ์ถ๊ฐ๋ฉ๋๋ค.

    > ๐ k-means++: [Scikit-learn](https://scikit-learn.org/stable/modules/clustering.html#k-means)์์ 'k-means++' ์ต์ ํ๋ฅผ ์ฌ์ฉํ  ์ ์๊ณ , ๋ฌด๊ฒ ์ค์ฌ์ (์ผ๋ฐ์ ์ธ) ๊ฑฐ๋ฆฌ๋ก ๊ฐ์ ๋จ์ด์ ธ์ ์ด๊ธฐํํ๋ฉด, ์๋ง ๋๋ค ์ด๊ธฐํ๋ณด๋ค ๋ ์ข์ ๊ฒฐ๊ณผ๋ก ์ด์ด์ง ์ ์์ต๋๋ค.

### Elbow method

์์ ์ ์ถ์ธกํ๋ ๊ฒ์ ๊ธฐ๋ฐ์ผ๋ก, 3๊ฐ ๋ธ๋ ์ฅ๋ฅด๋ฅผ ํ๊ฒํ ํ์ผ๋ฏ๋ก, 3๊ฒ ํด๋ฌ์คํฐ๋ฅผ ์ ํํด์ผ ๋์์ต๋๋ค. ๊ทธ๋ฌ๋ ๊ทธ๋ฌ์ด์ผ๋ง ํ๋์?

1. 'elbow method'์ ์ฌ์ฉํด์ ํ์ธํฉ๋๋ค.

    ```python
    plt.figure(figsize=(10,5))
    sns.lineplot(range(1, 11), wcss,marker='o',color='red')
    plt.title('Elbow')
    plt.xlabel('Number of clusters')
    plt.ylabel('WCSS')
    plt.show()
    ```

    ์ด์  ๋จ๊ณ์์ ๋ง๋ค์๋ `wcss` ๋ณ์๋ก, ์ต์  ํด๋ฌ์คํฐ ์๋ฅผ ๋ํ๋ผ elbow์ 'bend'๊ฐ ์ด๋์๋์ง ๋ณด์ฌ์ฃผ๋ ์ฐจํธ๋ฅผ ๋ง๋ญ๋๋ค. ์๋ง๋ 3 **์๋๋ค**!

    ![elbow method](../images/elbow.png)

## ์ฐ์ต - ํด๋ฌ์คํฐ ๋ณด์ด๊ธฐ

1. ํ๋ก์ธ์ค๋ฅผ ๋ค์ ์๋ํ์ฌ, ์ด ์์ ์ 3๊ฐ ํด๋ฌ์คํฐ๋ฅผ ๋ค์ ์ค์ ํ๊ณ , scatterplot์ผ๋ก ํด๋ฌ์คํฐ๋ฅผ ๋ณด์ฌ์ค๋๋ค:

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

1. ๋ชจ๋ธ ์ ํ๋๋ฅผ ํ์ธํฉ๋๋ค:

    ```python
    labels = kmeans.labels_
    
    correct_labels = sum(y == labels)
    
    print("Result: %d out of %d samples were correctly labeled." % (correct_labels, y.size))
    
    print('Accuracy score: {0:0.2f}'. format(correct_labels/float(y.size)))
    ```

    ์ด ๋ชจ๋ธ์ ์ ํ๋๋ ๋งค์ฐ ์ข์ง ์์ผ๋ฉฐ, ํด๋ฌ์คํฐ์ ํํ๊ฐ ์ ๊ทธ๋ฌ๋์ง ํํธ๋ฅผ ์ค๋๋ค.

    ![clusters](../images/clusters.png)

    ์ด ๋ฐ์ดํฐ๋ ๋งค์ฐ ๋ถ์์ ํ๋ฉฐ, ์๊ด ๊ด๊ณ๊ฐ ๋ฎ๊ณ  ์ด ๊ฐ ์ฌ์ด์ ํธ์ฐจ๊ฐ ์ปค์ ์ ํด๋ฌ์คํฐ๋  ์ ์์ต๋๋ค. ์ฌ์ค, ๋ง๋ค์ด์ง ํด๋ฌ์คํฐ๋ ์ ์ํ 3๊ฐ ์ฅ๋ฅด ์นดํ๊ณ ๋ฆฌ์ ํฌ๊ฒ ์ํฅ๋ฐ๊ฑฐ๋ ๋คํ๋ฆด ์ ์์ต๋๋ค. ํ์ต ํ๋ก์ธ์ค์๋๋ค!

    Scikit-learn ๋ฌธ์์, ํด๋ฌ์คํฐ๊ฐ ๋งค์ฐ ๋ชํํ์ง ์์ ๋ชจ๋ธ, 'variance' ๋ฌธ์ ๊ฐ ์์ต๋๋ค:

    ![problem models](../images/problems.png)
    > Infographic from Scikit-learn

## Variance

Variance๋ "the average of the squared differences from the Mean."์ผ๋ก ์ ์๋์์ต๋๋ค. [source](https://www.mathsisfun.com/data/standard-deviation.html) ์ด clustering ๋ฌธ์ ์ ์ปจํ์คํธ์์, ๋ฐ์ดํฐ์ ์ซ์๊ฐ ํ๊ท ์์ ๋๋ฌด ํฌ๊ฒ ์ดํ๋์ด ๋ฐ์ดํฐ๋ก ๋ํ๋๋๋ค.

โ ์ด ์ด์๋ฅผ ํด๊ฒฐํ  ๋ชจ๋  ๋ฐฉ์์ ์๊ฐํด๋ณด๋ ํ๋ฅญํ ์๊ฐ์๋๋ค. ๋ฐ์ดํฐ๋ฅผ ์กฐ๊ธ ํธ์ํด๋ณผ๊น์? ๋ค๋ฅธ ์ด์ ์ฌ์ฉํด๋ณผ๊น์? ๋ค๋ฅธ ์๊ณ ๋ฆฌ์ฆ์ ์ฌ์ฉํด๋ณผ๊น์? ํํธ: [scaling your data](https://www.mygreatlearning.com/blog/learning-data-science-with-k-means-clustering/)๋ก ๋ธ๋ฉ๋ผ์ด์ฆํ๊ณ  ๋ค๋ฅธ ์ปฌ๋ผ์ ํ์คํธํค๋ด๋๋ค.

> '[variance calculator](https://www.calculatorsoup.com/calculators/statistics/variance-calculator.php)'๋ก ์ข ๋ ๊ฐ๋์ ์ดํดํด๋ด๋๋ค.

---

## ๐ ๋์ 

ํ๋ผ๋ฏธํฐ๋ฅผ ํธ์ํ๋ฉด์, ๋ธํธ๋ถ์ผ๋ก ์๊ฐ์ ๋ณด๋๋๋ค. ๋ฐ์ดํฐ๋ฅผ ๋ ์ ๋ฆฌํด์ (์์๋ก, ์์๋ผ์ด์ด ์ ๊ฑฐ) ๋ชจ๋ธ์ ์ ํ๋๋ฅผ ๊ฐ์ ํ  ์ ์๋์? ๊ฐ์ค์น๋ก ์ฃผ์ด์ง ๋ฐ์ดํฐ ์ํ์์ ๋ ๊ฐ์ค์น๋ฅผ ์ค ์ ์์ต๋๋ค. ๊ด์ฐฎ์ ํด๋ฌ์คํฐ๋ฅผ ๋ง๋ค๊ธฐ ์ํค ์ด๋ค ๋ค๋ฅธ ์ผ์ ํ  ์ ์๋์?

ํํธ: ๋ฐ์ดํฐ๋ฅผ ๋ ํค์๋ด๋๋ค. ๊ฐ๊น์ด ๋ฒ์ ์กฐ๊ฑด์ ๋น์ทํ ๋ฐ์ดํฐ ์ด์ ๋ง๋ค๊ณ ์ ์ถ๊ฐํ๋ ํ์ค ์ค์ผ์ผ๋ง ์ฝ๋๋ฅผ ๋ธํธ๋ถ์ ์ฃผ์์ผ๋ก ๋จ๊ฒผ์ต๋๋ค. silhouette ์ ์๊ฐ ๋ฎ์์ง๋ ๋์, elbow ๊ทธ๋ํ์ 'kink'๊ฐ ์ฃผ๋ฆ ํด์ง๋ ๊ฒ์ ๋ณผ ์ ์์ต๋๋ค. ๋ฐ์ดํฐ๋ฅผ ์กฐ์ ํ์ง ์๊ณ  ๋จ๊ธฐ๋ฉด ๋ ๋ถ์ฐ๋ ๋ฐ์ดํฐ๊ฐ ๋ ๋ง์ ๊ฐ์ค์น๋ก ๋๋ฅผ ์ ์๋ค๋ ์ด์ ์๋๋ค. [here](https://stats.stackexchange.com/questions/21222/are-mean-normalization-and-feature-scaling-needed-for-k-means-clustering/21226#21226) ์ด ๋ฌธ์ ๋ฅผ ์กฐ๊ธ ๋ ์ฝ์ด๋ด๋๋ค.

## [๊ฐ์ ํ ํด์ฆ](https://gray-sand-07a10f403.1.azurestaticapps.net/quiz/30/)

## ๊ฒํ  & ์๊ธฐ์ฃผ๋ ํ์ต

[such as this one](https://user.ceng.metu.edu.tr/~akifakkus/courses/ceng574/k-means/)๊ฐ์ K-Means ์๋ฎฌ๋ ์ดํฐ๋ฅผ ์ฐพ์๋ด๋๋ค. ์ด ๋๊ตฌ๋ก ์ํ ๋ฐ์ดํฐ ํฌ์ธํธ๋ฅผ ์๊ฐํํ๊ณ  ๋ฌด๊ฒ ์ค์ฌ์ ๊ฒฐ์ ํ  ์ ์์ต๋๋ค. ๋ฐ์ดํฐ์ ๋๋ค์ฑ, ํด๋ฌ์คํฐ ์์ ๋ฌด๊ฒ ์ค์ฌ ์๋ฅผ ๊ณ ์น  ์ ์์ต๋๋ค. ๋ฐ์ดํฐ๋ฅผ ๊ทธ๋ฃน์ผ๋ก ๋ฌถ๊ธฐ ์ํ ์์ด๋์ด๋ฅผ ์ป๋ ๊ฒ ๋์์ด ๋๋์?

๋ํ, Stanford ์ [this handout on K-Means](https://stanford.edu/~cpiech/cs221/handouts/kmeans.html) ์ ์ฐพ์๋ด๋๋ค.

## ๊ณผ์ 

[Try different clustering methods](../assignment.md)
