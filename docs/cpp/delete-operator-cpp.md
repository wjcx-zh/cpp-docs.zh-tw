---
title: delete 运算符 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- delete_cpp
dev_langs:
- C++
helpviewer_keywords:
- delete keyword [C++], syntax
- delete keyword [C++], deallocating objects
- delete keyword [C++]
ms.assetid: de39c900-3f57-489c-9598-dcb73c4b3930
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f4f563a424fd5a019b2094f931236f4af6f0ecb4
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39407724"
---
# <a name="delete-operator-c"></a>delete 運算子 (C++)
取消配置記憶體區塊。  
  
## <a name="syntax"></a>語法  
  
```  
[::] delete cast-expression  
[::] delete [ ] cast-expression  
```  
  
## <a name="remarks"></a>備註  
 *轉型運算式*引數必須是先前建立的物件配置的記憶體區塊的指標[new 運算子](../cpp/new-operator-cpp.md)。 **刪除**運算子的結果是型別**void** ，因此不會傳回值。 例如:   
  
```cpp 
CDialog* MyDialog = new CDialog;  
// use MyDialog  
delete MyDialog;  
```  
  
 使用**刪除**不會配置與物件的指標**新**會產生無法預期的結果。 不過，您可以使用**刪除**值為 0 的指標。 此佈建表示，當**新**失敗時，刪除失敗的結果會傳回 0**新**作業不會有影響。 請參閱[新和 delete 運算子](../cpp/new-and-delete-operators.md)如需詳細資訊。  
  
 **新**並**刪除**運算子也可以用於內建類型，包括陣列。 如果 `pointer` 指的是陣列，請在 `pointer` 前面放置空大括號：  
  
```cpp 
int* set = new int[100];  
//use set[]  
delete [] set;  
```  
  
 使用**刪除**運算子，在物件解除配置其記憶體。 在刪除物件之後將指標取值的程式可能會有無法預期的結果或損毀。  
  
 當**刪除**是用來取消配置 c + + 類別物件，物件的解構函式呼叫之前 （如果物件具有解構函式），會解除配置物件的記憶體。  
  
 如果運算元**刪除**操作員是可修改左值之後刪除物件,，其值為未定義。  
  
## <a name="using-delete"></a>使用 delete  
 有兩種語法變化[delete 運算子](../cpp/delete-operator-cpp.md)： 一個用於單一物件，而另一個則用於物件的陣列。 下列程式碼片段示範兩者不同之處：  
  
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
  
 下列兩種情況會產生未定義的結果：對物件使用陣列形式的刪除 (delete [ ])，以及對陣列使用非陣列形式的刪除。  
  
## <a name="example"></a>範例  
 如需使用的範例**刪除**，請參閱[new 運算子](../cpp/new-operator-cpp.md)。  
  
## <a name="how-delete-works"></a>delete 運作方式  
 Delete 運算子會叫用函式**運算子 delete**。  
  
 不是類別類型的物件 ([類別](../cpp/class-cpp.md)，[結構](../cpp/struct-cpp.md)，或[union](../cpp/unions.md))，會叫用全域 delete 運算子。 對於類別類型的物件，如果刪除運算式是以一元範圍解析運算子 (::) 開頭，則會在全域範圍中解析解除配置函式的名稱。 否則，如果指標不是 Null，delete 運算子會在解除配置記憶體之前叫用物件的解構函式。 delete 運算子可以依類別來定義；如果指定類別沒有這類定義，會叫用全域 delete 運算子。 如果使用刪除運算式來解除配置靜態類型包含虛擬解構函式的類別物件，則會透過該物件之動態類型的虛擬解構函式來解析解除配置函式。  
  
## <a name="see-also"></a>另請參閱  
 [具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)   
 [關鍵字](../cpp/keywords-cpp.md)   
 [new 和 delete 運算子](../cpp/new-and-delete-operators.md)   