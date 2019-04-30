---
title: HOW TO：定義移動建構函式和移動指派運算子 (C++)
ms.date: 03/05/2018
helpviewer_keywords:
- move constructor [C++]
ms.assetid: e75efe0e-4b74-47a9-96ed-4e83cfc4378d
ms.openlocfilehash: b601c53c01940fe110036d569e0be9d43a123a91
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345020"
---
# <a name="move-constructors-and-move-assignment-operators-c"></a>移動建構函式和移動指派運算子 (C++)

本主題說明如何撰寫*移動建構函式*和移動指派運算子C++類別。 移動建構函式可讓要移至左值，而不複製右值物件所擁有的資源。 如需有關移動語意的詳細資訊，請參閱 < [Rvalue 參考宣告子： & &](../cpp/rvalue-reference-declarator-amp-amp.md)。

這個主題是以下列管理記憶體緩衝區的 C++ 類別 `MemoryBlock` 為基礎。

```cpp
// MemoryBlock.h
#pragma once
#include <iostream>
#include <algorithm>

class MemoryBlock
{
public:

   // Simple constructor that initializes the resource.
   explicit MemoryBlock(size_t length)
      : _length(length)
      , _data(new int[length])
   {
      std::cout << "In MemoryBlock(size_t). length = "
                << _length << "." << std::endl;
   }

   // Destructor.
   ~MemoryBlock()
   {
      std::cout << "In ~MemoryBlock(). length = "
                << _length << ".";

      if (_data != nullptr)
      {
         std::cout << " Deleting resource.";
         // Delete the resource.
         delete[] _data;
      }

      std::cout << std::endl;
   }

   // Copy constructor.
   MemoryBlock(const MemoryBlock& other)
      : _length(other._length)
      , _data(new int[other._length])
   {
      std::cout << "In MemoryBlock(const MemoryBlock&). length = "
                << other._length << ". Copying resource." << std::endl;

      std::copy(other._data, other._data + _length, _data);
   }

   // Copy assignment operator.
   MemoryBlock& operator=(const MemoryBlock& other)
   {
      std::cout << "In operator=(const MemoryBlock&). length = "
                << other._length << ". Copying resource." << std::endl;

      if (this != &other)
      {
         // Free the existing resource.
         delete[] _data;

         _length = other._length;
         _data = new int[_length];
         std::copy(other._data, other._data + _length, _data);
      }
      return *this;
   }

   // Retrieves the length of the data resource.
   size_t Length() const
   {
      return _length;
   }

private:
   size_t _length; // The length of the resource.
   int* _data; // The resource.
};
```

下列程序說明如何撰寫 C++ 類別的移動建構函式和移動指派運算子。

### <a name="to-create-a-move-constructor-for-a-c-class"></a>建立 C++ 類別的移動建構函式

1. 定義空的建構函式方法，該方法會接受以類別類型的右值參考做為其參數，如下列範例所示範：

    ```cpp
    MemoryBlock(MemoryBlock&& other)
       : _data(nullptr)
       , _length(0)
    {
    }
    ```

1. 在移動建構函式中，將類別資料成員從來源物件指派給將建構的物件：

    ```cpp
    _data = other._data;
    _length = other._length;
    ```

1. 將來源物件的資料成員指派為預設值。 這樣可防止解構函式多次釋放資源 (例如記憶體)：

    ```cpp
    other._data = nullptr;
    other._length = 0;
    ```

### <a name="to-create-a-move-assignment-operator-for-a-c-class"></a>建立 C++ 類別的移動指派運算子

1. 定義空的指派運算子，該運算子會接受以類別類型的右值參考做為其參數，並傳回對類別類型的參考，如下列範例所示範：

    ```cpp
    MemoryBlock& operator=(MemoryBlock&& other)
    {
    }
    ```

1. 在移動指派運算子中，如果您嘗試將物件指派給其本身，請新增不執行任何作業的條件陳述式。

    ```cpp
    if (this != &other)
    {
    }
    ```

1. 在條件陳述式中，從所指派的物件釋放所有資源 (例如記憶體)。

   下列範例會從所指派的物件釋放 `_data` 成員：

    ```cpp
    // Free the existing resource.
    delete[] _data;
    ```

   依照第一個程序的步驟 2 和步驟 3，將資料成員從來源物件傳送至將建構的物件：

    ```cpp
    // Copy the data pointer and its length from the
    // source object.
    _data = other._data;
    _length = other._length;

    // Release the data pointer from the source object so that
    // the destructor does not free the memory multiple times.
    other._data = nullptr;
    other._length = 0;
    ```

1. 傳回目前物件的參考，如下列範例所示範：

    ```cpp
    return *this;
    ```

## <a name="example"></a>範例

下列範例示範 `MemoryBlock` 類別的完整移動建構函式和移動指派運算子：

```cpp
// Move constructor.
MemoryBlock(MemoryBlock&& other)
   : _data(nullptr)
   , _length(0)
{
   std::cout << "In MemoryBlock(MemoryBlock&&). length = "
             << other._length << ". Moving resource." << std::endl;

   // Copy the data pointer and its length from the
   // source object.
   _data = other._data;
   _length = other._length;

   // Release the data pointer from the source object so that
   // the destructor does not free the memory multiple times.
   other._data = nullptr;
   other._length = 0;
}

// Move assignment operator.
MemoryBlock& operator=(MemoryBlock&& other)
{
   std::cout << "In operator=(MemoryBlock&&). length = "
             << other._length << "." << std::endl;

   if (this != &other)
   {
      // Free the existing resource.
      delete[] _data;

      // Copy the data pointer and its length from the
      // source object.
      _data = other._data;
      _length = other._length;

      // Release the data pointer from the source object so that
      // the destructor does not free the memory multiple times.
      other._data = nullptr;
      other._length = 0;
   }
   return *this;
}
```

## <a name="example"></a>範例

下列範例示範移動語意如何改善應用程式的效能。 此範例會在向量物件中加入兩個元素，然後在兩個現有元素之間插入新的元素。 `vector`類別會使用移動語意，以有效率地執行插入作業，藉由移動而非複製向量的元素。

```cpp
// rvalue-references-move-semantics.cpp
// compile with: /EHsc
#include "MemoryBlock.h"
#include <vector>

using namespace std;

int main()
{
   // Create a vector object and add a few elements to it.
   vector<MemoryBlock> v;
   v.push_back(MemoryBlock(25));
   v.push_back(MemoryBlock(75));

   // Insert a new element into the second position of the vector.
   v.insert(v.begin() + 1, MemoryBlock(50));
}
```

這個範例會產生下列輸出：

```Output
In MemoryBlock(size_t). length = 25.
In MemoryBlock(MemoryBlock&&). length = 25. Moving resource.
In ~MemoryBlock(). length = 0.
In MemoryBlock(size_t). length = 75.
In MemoryBlock(MemoryBlock&&). length = 25. Moving resource.
In ~MemoryBlock(). length = 0.
In MemoryBlock(MemoryBlock&&). length = 75. Moving resource.
In ~MemoryBlock(). length = 0.
In MemoryBlock(size_t). length = 50.
In MemoryBlock(MemoryBlock&&). length = 50. Moving resource.
In MemoryBlock(MemoryBlock&&). length = 50. Moving resource.
In operator=(MemoryBlock&&). length = 75.
In operator=(MemoryBlock&&). length = 50.
In ~MemoryBlock(). length = 0.
In ~MemoryBlock(). length = 0.
In ~MemoryBlock(). length = 25. Deleting resource.
In ~MemoryBlock(). length = 50. Deleting resource.
In ~MemoryBlock(). length = 75. Deleting resource.
```

Visual Studio 2010 之前, 此範例會產生下列輸出：

```Output
In MemoryBlock(size_t). length = 25.
In MemoryBlock(const MemoryBlock&). length = 25. Copying resource.
In ~MemoryBlock(). length = 25. Deleting resource.
In MemoryBlock(size_t). length = 75.
In MemoryBlock(const MemoryBlock&). length = 25. Copying resource.
In ~MemoryBlock(). length = 25. Deleting resource.
In MemoryBlock(const MemoryBlock&). length = 75. Copying resource.
In ~MemoryBlock(). length = 75. Deleting resource.
In MemoryBlock(size_t). length = 50.
In MemoryBlock(const MemoryBlock&). length = 50. Copying resource.
In MemoryBlock(const MemoryBlock&). length = 50. Copying resource.
In operator=(const MemoryBlock&). length = 75. Copying resource.
In operator=(const MemoryBlock&). length = 50. Copying resource.
In ~MemoryBlock(). length = 50. Deleting resource.
In ~MemoryBlock(). length = 50. Deleting resource.
In ~MemoryBlock(). length = 25. Deleting resource.
In ~MemoryBlock(). length = 50. Deleting resource.
In ~MemoryBlock(). length = 75. Deleting resource.
```

這個使用移動語意的範例版本比不使用移動語意的版本更有效率，因為前者執行較少的複製、記憶體配置和記憶體解除配置作業。

## <a name="robust-programming"></a>穩固程式設計

為避免資源流失，請一律釋放移動指派運算子中的資源 (例如記憶體、檔案控制代碼和通訊端)。

為避免解構資源後無法復原，請適當地處理移動指派運算子中的自我指派。

如果您同時為類別提供移動建構函式和移動指派運算子，可以撰寫移動建構函式來呼叫移動指派運算子，藉此去除冗餘碼。 下列範例示範呼叫移動指派運算子的修訂版移動建構函式。

```cpp
// Move constructor.
MemoryBlock(MemoryBlock&& other)
   : _data(nullptr)
   , _length(0)
{
   *this = std::move(other);
}
```

[Std:: move](../standard-library/utility-functions.md#move)函式會保留的右值屬性*其他*參數。

## <a name="see-also"></a>另請參閱

[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)<br/>
[std::move](../standard-library/utility-functions.md#move)