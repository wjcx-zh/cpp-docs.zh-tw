---
title: "delete 運算子 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- delete_cpp
- delete
dev_langs:
- C++
helpviewer_keywords:
- delete keyword [C++], syntax
- delete keyword [C++], deallocating objects
- delete keyword [C++]
ms.assetid: de39c900-3f57-489c-9598-dcb73c4b3930
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: bfc2587b4d55ae0147adf797990139356d44cd30
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="delete-operator-c"></a>delete 運算子 (C++)
取消配置記憶體區塊。  
  
## <a name="syntax"></a>語法  
  
```  
[::] delete cast-expression  
[::] delete [ ] cast-expression  
```  
  
## <a name="remarks"></a>備註  
 *轉型運算式*引數必須是先前建立的物件配置的記憶體區塊的指標[new 運算子](../cpp/new-operator-cpp.md)。 **刪除**運算子的結果類型是`void`，因此不會傳回值。 例如:   
  
```  
CDialog* MyDialog = new CDialog;  
// use MyDialog  
delete MyDialog;  
```  
  
 使用**刪除**上不會配置與物件的指標**新**產生無法預期的結果。 不過，您可以使用**刪除**值為 0 的指標。 這項佈建表示，當**新**失敗時，刪除失敗結果會傳回 0**新**是無害的作業。 請參閱[新和 delete 運算子](../cpp/new-and-delete-operators.md)如需詳細資訊。  
  
 **新**和**刪除**運算子也可以用於內建類型，包括陣列。 如果 `pointer` 指的是陣列，請在 `pointer` 前面放置空大括號：  
  
```  
int* set = new int[100];  
//use set[]  
delete [] set;  
```  
  
 使用**刪除**物件上的運算子取消配置其記憶體。 在刪除物件之後將指標取值的程式可能會有無法預期的結果或損毀。  
  
 當**刪除**是用來取消配置 c + + 類別物件，此物件的解構函式之前，會呼叫 （如果物件具有解構函式），會取消配置物件的記憶體。  
  
 如果運算元**刪除**運算子是可修改左值，其值在刪除物件之後為未定義。  
  
## <a name="using-delete"></a>使用 delete  
 有兩種語法變化[delete 運算子](../cpp/delete-operator-cpp.md)： 一個適用於單一物件，而另一個則用於物件的陣列。 下列程式碼片段示範兩者不同之處：  
  
```  
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
 

