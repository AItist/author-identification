Kaggle Author Identification Competition processed by CNN
Share code and discuss insights to identify horror authors from their writings

https://www.kaggle.com/c/spooky-author-identification




<hr/>
####Preprocessing 3rd####
<hr/>

Third, label data into one hot encoding such as :

ESP = [1 0 0]
HPL = [0 1 0]
MWS = [0 0 1]

and save data into pickle format

```
def load_data_and_labels_another():
    """
    Loads MR polarity data from files, splits the data into words and generates labels.
    Returns split sentences and labels.
    """
    x_text = []
    y = []
    one_hot_vector = [0,0,0]
    labels = {}
    topics = ['ESP','HPL' , 'MWS']
    for idx, topic in enumerate(topics):
        clean_questions = list(open(topic + ".txt", mode = 'rb').readlines())
        clean_questions = [s.strip() for s in clean_questions]
        x_text = x_text + clean_questions
        print (len(x_text))
        if topic == 'ESP':
            y = y + [[1,0,0] for _ in clean_questions]
        elif topic == 'HPL':
            y = y + [[0,1,0] for _ in clean_questions]
        elif topic == 'MWS':
            y = y + [[0,0,1] for _ in clean_questions]        # print labels

    y = np.array(y)
    print(len(y))
    return [x_text, y]

if __name__ == "__main__":

    word_indices = []
    y = []
    word_indices, y = load_data_and_labels_another()

    word_index_pickle = open('new_data_pickle', 'wb')
    pickling = {'x': word_indices, 'y': y}
    pickle.dump(pickling, word_index_pickle)

```

After this sequence, you can get data(as pickle format) to generate embedding matrix



