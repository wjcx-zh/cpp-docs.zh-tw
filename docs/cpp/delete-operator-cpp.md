---
title: delete 運算子 (C++)
ms.date: 08/12/2019
f1_keywords:
- delete_cpp
helpviewer_keywords:
- delete keyword [C++], syntax
- delete keyword [C++], deallocating objects
- delete keyword [C++]
ms.assetid: de39c900-3f57-489c-9598-dcb73c4b3930
ms.openlocfilehash: 19f92e2aa62adf1ede4c0e6ab1187fd9e4106e68
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221688"
---
# <a name="delete-operator-c"></a>delete 運算子 (C++)

取消配置記憶體區塊。

## <a name="syntax"></a>語法

> [ `::` ] `delete` *cast 運算式*\
> [ `::` ] `delete []` *cast 運算式*

## <a name="remarks"></a>備註

*Cast 運算式*引數必須是先前針對使用[new 運算子](../cpp/new-operator-cpp.md)所建立之物件所配置的記憶體區塊的指標。 **`delete`** 運算子具有類型的結果 **`void`** ，因此不會傳回值。 例如：

```cpp
CDialog* MyDialog = new CDialog;
// use MyDialog
delete MyDialog;
```

**`delete`** 在未配置的物件指標上使用，會 **`new`** 產生無法預期的結果。 不過，您可以 **`delete`** 在值為0的指標上使用。 這項布建表示，當失敗時傳回 **`new`** 0 時，刪除失敗作業的結果 **`new`** 是無害的。 如需詳細資訊，請參閱[new 和 Delete 運算子](../cpp/new-and-delete-operators.md)。

**`new`** 和 **`delete`** 運算子也可以用於內建類型，包括陣列。 如果 `pointer` 參考陣列，請在之前放置空的括弧（ `[]` ） `pointer` ：

```cpp
int* set = new int[100];
//use set[]
delete [] set;
```

**`delete`** 在物件上使用運算子會取消配置其記憶體。 在刪除物件之後將指標取值的程式可能會有無法預期的結果或損毀。

當 **`delete`** 用來解除配置 c + + 類別物件的記憶體時，會在解除配置物件的記憶體之前呼叫物件的析構函式（如果物件具有析構函式）。

如果運算子的運算元 **`delete`** 是可修改的左值，則在刪除物件之後，其值會是未定義的。

如果指定了[/sdl （啟用其他安全性檢查）](/cpp/build/reference/sdl-enable-additional-security-checks)編譯器選項，則在 **`delete`** 刪除物件之後，運算子的運算元會設定為不正確值。

## <a name="using-delete"></a>使用 delete

[Delete 運算子](../cpp/delete-operator-cpp.md)有兩種語法變體：一個用於單一物件，另一個用於物件陣列。 下列程式碼片段顯示它們的差異：

```cpp
// expre_Using_delete.cpp
struct UDType
{
};

int main()
{
   // Allocate a user-defined object, UDObject, and an object
   //  of type double on the free store using the
   //  new operator.
   UDType *UDObject = new UDType;
   double *dObject = new double;
   // Delete the two objects.
   delete UDObject;
   delete dObject;
   // Allocate an array of user-defined objects on the
   // free store using the new operator.
   UDType (*UDArr)[7] = new UDType[5][7];
   // Use the array syntax to delete the array of objects.
   delete [] UDArr;
}
```

下列兩種情況會產生未定義的結果：在物件上使用陣列形式的 delete （ `delete []` ），並在陣列上使用 nonarray 形式的 delete。

## <a name="example"></a>範例

如需使用的範例 **`delete`** ，請參閱[new 運算子](../cpp/new-operator-cpp.md)。

## <a name="how-delete-works"></a>delete 運作方式

Delete 運算子會叫用函數**operator delete**。

對於不屬於類別類型（[類別](../cpp/class-cpp.md)、[結構](../cpp/struct-cpp.md)[或等](../cpp/unions.md)位）的物件，會叫用全域 delete 運算子。 對於類別類型的物件，如果刪除運算式是以一元範圍解析運算子（）開頭，則會在全域範圍中解析解除配置函式的名稱 `::` 。 否則，如果指標不是 Null，delete 運算子會在解除配置記憶體之前叫用物件的解構函式。 delete 運算子可以依類別來定義；如果指定類別沒有這類定義，會叫用全域 delete 運算子。 如果使用刪除運算式來解除配置靜態類型包含虛擬解構函式的類別物件，則會透過該物件之動態類型的虛擬解構函式來解析解除配置函式。

## <a name="see-also"></a>另請參閱

[具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)\
[字](../cpp/keywords-cpp.md)\
[new 和 delete 運算子](../cpp/new-and-delete-operators.md)
