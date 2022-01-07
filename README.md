# Not-ONLY-The-price-of-Books
<p style='font-size: 18px;font-weight:bold'>Transform</p>


- One of the best methodologies for building a fully managed DAG using [TFX](https://www.tensorflow.org/tfx).


- This [DAG](https://en.wikipedia.org/wiki/Directed_acyclic_graph)  is built based on Feature Engineering:

    1. Input Layers:

        A. **Ratings**: it takes the rating of the customers about a book – the `scrape_Ratings` responsible for scraping the float value out of the binary tensors then scales the values using z-score in a Data Distributed manner and memory contributed way using [TF.Transform](https://www.tensorflow.org/tfx/tutorials/transform/census).

        B. **Reviews**: it similars to `Ratings` but the difference here is, using min-max normalization since the reviews have discrete values also by using TF.Transform. (TF. Transform is way better than Sklearn for preprocessing. Sklearn eats the memory, crucially.

        C. **BookCategory**: is a vocabulary list Built based on the [TensorFlow vocabulary file](https://www.tensorflow.org/api_docs/python/tf/feature_column/categorical_column_with_vocabulary_file).

        D. **Genre**: Similar to BookCategory.

    2. **DenseFeatures**: Responsible for creating `feature_column` layer out of all these layers (i.e embedding feature columns which are used after crossing all these features together.


- **How did I choose these layers out of all the other features?**

    * I can't forget to mention my favorite API of all times: [**TensorFlow Data Validation (TFDV)**.](https://www.tensorflow.org/tfx/data_validation/get_started) This API is one of the open-source APIs based on [**Facets**](https://pair-code.github.io/facets/). Using it helps me to discover the anomalies, Skew, Distribution Skew, Drifts, Data Interpolation & Extrapolation, etc. You will definitely want to use it when you want to visualize and analyze your data.
