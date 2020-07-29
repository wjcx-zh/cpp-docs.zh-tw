---
title: 樣板特製化 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- partial specialization of class templates
ms.assetid: f3c67c0b-3875-434a-b8d8-bb47e99cf4f0
ms.openlocfilehash: 17f1f15a5356d760119123214e939a7dd2d1fbaf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223573"
---
# <a name="template-specialization-c"></a>樣板特製化 (C++)

類別樣板可以部分特製化，而產生的類別仍然是樣板。 部分特製化可以視情況針對特定類型部分自訂樣板程式碼，例如：

- 樣板可以有多個類型，只需特製化其中一部分。 結果是在其他類型參數化的樣板。

- 一個樣板只能有一個類型，不過，指標、參考、成員指標或函式指標類型都需要特製化。 特製化本身仍然是指向類型或參考類型的樣板。

## <a name="example"></a>範例

```cpp
// partial_specialization_of_class_templates.cpp
template <class T> struct PTS {
   enum {
      IsPointer = 0,
      IsPointerToDataMember = 0
   };
};

template <class T> struct PTS<T*> {
   enum {
      IsPointer = 1,
      IsPointerToDataMember = 0
   };
};

template <class T, class U> struct PTS<T U::*> {
   enum {
      IsPointer = 0,
      IsPointerToDataMember = 1
   };
};

struct S{};

extern "C" int printf_s(const char*,...);

int main() {
   printf_s("PTS<S>::IsPointer == %d PTS<S>::IsPointerToDataMember == %d\n",
           PTS<S>::IsPointer, PTS<S>:: IsPointerToDataMember);
   printf_s("PTS<S*>::IsPointer == %d PTS<S*>::IsPointerToDataMember ==%d\n"
           , PTS<S*>::IsPointer, PTS<S*>:: IsPointerToDataMember);
   printf_s("PTS<int S::*>::IsPointer == %d PTS"
           "<int S::*>::IsPointerToDataMember == %d\n",
           PTS<int S::*>::IsPointer, PTS<int S::*>::
           IsPointerToDataMember);
}
```

```Output
PTS<S>::IsPointer == 0 PTS<S>::IsPointerToDataMember == 0
PTS<S*>::IsPointer == 1 PTS<S*>::IsPointerToDataMember ==0
PTS<int S::*>::IsPointer == 0 PTS<int S::*>::IsPointerToDataMember == 1
```

## <a name="example"></a>範例

如果您的樣板集合類別接受任何類型 `T` ，您可以建立接受任何指標類型的部分特製化 `T*` 。 下列程式碼示範集合類別樣板 `Bag` 和指標類型的部分特製化，其中該集合會在將指標類型複製到陣列之前取值指標類型。 然後，該集合會儲存指向的值。 若使用原始樣板，只能將指標本身儲存在集合中，因此資料容易遭到刪除或修改。 在這種特殊指標版本的集合中，會在 `add` 方法中新增檢查 null 指標的程式碼。

```cpp
// partial_specialization_of_class_templates2.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

// Original template collection class.
template <class T> class Bag {
   T* elem;
   int size;
   int max_size;

public:
   Bag() : elem(0), size(0), max_size(1) {}
   void add(T t) {
      T* tmp;
      if (size + 1 >= max_size) {
         max_size *= 2;
         tmp = new T [max_size];
         for (int i = 0; i < size; i++)
            tmp[i] = elem[i];
         tmp[size++] = t;
         delete[] elem;
         elem = tmp;
      }
      else
         elem[size++] = t;
   }

   void print() {
      for (int i = 0; i < size; i++)
         cout << elem[i] << " ";
      cout << endl;
   }
};

// Template partial specialization for pointer types.
// The collection has been modified to check for NULL
// and store types pointed to.
template <class T> class Bag<T*> {
   T* elem;
   int size;
   int max_size;

public:
   Bag() : elem(0), size(0), max_size(1) {}
   void add(T* t) {
      T* tmp;
      if (t == NULL) {   // Check for NULL
         cout << "Null pointer!" << endl;
         return;
      }

      if (size + 1 >= max_size) {
         max_size *= 2;
         tmp = new T [max_size];
         for (int i = 0; i < size; i++)
            tmp[i] = elem[i];
         tmp[size++] = *t;  // Dereference
         delete[] elem;
         elem = tmp;
      }
      else
         elem[size++] = *t; // Dereference
   }

   void print() {
      for (int i = 0; i < size; i++)
         cout << elem[i] << " ";
      cout << endl;
   }
};

int main() {
   Bag<int> xi;
   Bag<char> xc;
   Bag<int*> xp; // Uses partial specialization for pointer types.

   xi.add(10);
   xi.add(9);
   xi.add(8);
   xi.print();

   xc.add('a');
   xc.add('b');
   xc.add('c');
   xc.print();

   int i = 3, j = 87, *p = new int[2];
   *p = 8;
   *(p + 1) = 100;
   xp.add(&i);
   xp.add(&j);
   xp.add(p);
   xp.add(p + 1);
   p = NULL;
   xp.add(p);
   xp.print();
}
```

```Output
10 9 8
a b c
Null pointer!
3 87 8 100
```

## <a name="example"></a>範例

下列範例會定義一個樣板類別，它會接受兩個類型的配對，然後定義該樣板類別的部分特製化，讓其中一個類型為 **`int`** 。 特製化會額外定義排序方法，這個方法會根據整數實作簡單的反昇排序。

```cpp
// partial_specialization_of_class_templates3.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

template <class Key, class Value> class Dictionary {
   Key* keys;
   Value* values;
   int size;
   int max_size;
public:
   Dictionary(int initial_size) :  size(0) {
      max_size = 1;
      while (initial_size >= max_size)
         max_size *= 2;
      keys = new Key[max_size];
      values = new Value[max_size];
   }
   void add(Key key, Value value) {
      Key* tmpKey;
      Value* tmpVal;
      if (size + 1 >= max_size) {
         max_size *= 2;
         tmpKey = new Key [max_size];
         tmpVal = new Value [max_size];
         for (int i = 0; i < size; i++) {
            tmpKey[i] = keys[i];
            tmpVal[i] = values[i];
         }
         tmpKey[size] = key;
         tmpVal[size] = value;
         delete[] keys;
         delete[] values;
         keys = tmpKey;
         values = tmpVal;
      }
      else {
         keys[size] = key;
         values[size] = value;
      }
      size++;
   }

   void print() {
      for (int i = 0; i < size; i++)
         cout << "{" << keys[i] << ", " << values[i] << "}" << endl;
   }
};

// Template partial specialization: Key is specified to be int.
template <class Value> class Dictionary<int, Value> {
   int* keys;
   Value* values;
   int size;
   int max_size;
public:
   Dictionary(int initial_size) :  size(0) {
      max_size = 1;
      while (initial_size >= max_size)
         max_size *= 2;
      keys = new int[max_size];
      values = new Value[max_size];
   }
   void add(int key, Value value) {
      int* tmpKey;
      Value* tmpVal;
      if (size + 1 >= max_size) {
         max_size *= 2;
         tmpKey = new int [max_size];
         tmpVal = new Value [max_size];
         for (int i = 0; i < size; i++) {
            tmpKey[i] = keys[i];
            tmpVal[i] = values[i];
         }
         tmpKey[size] = key;
         tmpVal[size] = value;
         delete[] keys;
         delete[] values;
         keys = tmpKey;
         values = tmpVal;
      }
      else {
         keys[size] = key;
         values[size] = value;
      }
      size++;
   }

   void sort() {
      // Sort method is defined.
      int smallest = 0;
      for (int i = 0; i < size - 1; i++) {
         for (int j = i; j < size; j++) {
            if (keys[j] < keys[smallest])
               smallest = j;
         }
         swap(keys[i], keys[smallest]);
         swap(values[i], values[smallest]);
      }
   }

   void print() {
      for (int i = 0; i < size; i++)
         cout << "{" << keys[i] << ", " << values[i] << "}" << endl;
   }
};

int main() {
   Dictionary<char*, char*>* dict = new Dictionary<char*, char*>(10);
   dict->print();
   dict->add("apple", "fruit");
   dict->add("banana", "fruit");
   dict->add("dog", "animal");
   dict->print();

   Dictionary<int, char*>* dict_specialized = new Dictionary<int, char*>(10);
   dict_specialized->print();
   dict_specialized->add(100, "apple");
   dict_specialized->add(101, "banana");
   dict_specialized->add(103, "dog");
   dict_specialized->add(89, "cat");
   dict_specialized->print();
   dict_specialized->sort();
   cout << endl << "Sorted list:" << endl;
   dict_specialized->print();
}
```

```Output
{apple, fruit}
{banana, fruit}
{dog, animal}
{100, apple}
{101, banana}
{103, dog}
{89, cat}

Sorted list:
{89, cat}
{100, apple}
{101, banana}
{103, dog}
```
