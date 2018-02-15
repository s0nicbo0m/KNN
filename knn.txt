import math
import random
import operator
import unicsvcode


def shuffle(idata):
    random.shuffle(idata)
    train_data=idata[:int(0.7*30)]
    test_data=idata[int(0.7*30):]
    return test_data,train_data


def accuracy(test_data):
    correct=0
    for i in test_data:
        if(i[35]==i[34]):
            correct=correct+1;
    accuracy=float(correct/len(test_data))*100
    return accuracy


def eu(a,b):
    d=0.0
    for i in range (len(a)-1):
        d=d+pow((float(a[i])-float(b[i])),2)
    d=math.sqrt(d)
    return d


def knn_predict(test_data, train_data, k_value):
    for i in test_data:
        eu_Distance =[]
        knn = []
        good = 0

        bad = 0
        for j in train_data:
            eu_dist = eu(i, j)
            eu_Distance.append((j[34], eu_dist))
            eu_Distance.sort(key = operator.itemgetter(1))
            knn = eu_Distance[:k_value]
            for k in knn:
                if k[0] =='g':
                    good += 1
                else:
                    bad +=1
        if good > bad:
            i.append('g')
        elif good < bad:
            i.append('b')
        else:
            i.append('NaN')

 def accuracy(test_data):
    correct=0
    for i in test_data:
        if(i[35]==i[34]):
            correct=correct+1;
    accuracy=float(correct/len(test_data))*100
    return accuracy


dataset = getdata('ionosphere.csv')  
tr_dataset, te_dataset = shuffle(dataset)                  
knn_predict(test_dataset, train_dataset, 25)    #taking k=25   
accuracy(te_data)
print(accuracy)