---
title: "delete 運算子 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "delete_cpp"
  - "delete"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "delete 關鍵字 [C++]"
  - "delete 關鍵字 [C++], 解除配置物件"
  - "delete 關鍵字 [C++], 語法"
ms.assetid: de39c900-3f57-489c-9598-dcb73c4b3930
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# delete 運算子 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取消配置記憶體區塊。  
  
## 語法  
  
```  
[::] delete cast-expression  
[::] delete [ ] cast-expression  
```  
  
## 備註  
 *cast\-expression* 引數必須是先前配置給物件的記憶體區塊指標，而物件是使用 [new 運算子](../cpp/new-operator-cpp.md)所建立。  **delete** 運算子具有類型 `void` 的結果，因此不會傳回值。  例如:  
  
```  
CDialog* MyDialog = new CDialog;  
// use MyDialog  
delete MyDialog;  
```  
  
 對未使用 **new** 配置之物件的指標使用 **delete** 會產生無法預期的結果。  不過，您可以對值為 0 的指標使用 **delete**。  這項佈建表示，如果 **new** 在失敗時傳回 0，則刪除失敗 **new** 作業的結果無害。  如需詳細資訊，請參閱 [new 和 delete 運算子](../cpp/new-and-delete-operators.md)。  
  
 **new** 和 **delete** 運算子也可以用於內建類型 \(包括陣列\)。  如果 `pointer` 指的是陣列，請在 `pointer` 前面放置空大括號：  
  
```  
int* set = new int[100];  
//use set[]  
delete [] set;  
```  
  
 對物件使用 **delete** 運算子會取消配置其記憶體。  在刪除物件之後將指標取值的程式可能會有無法預期的結果或損毀。  
  
 **delete** 用來取消配置 C\+\+ 類別物件的記憶體時，會在取消配置物件的記憶體 \(如果物件具有解構函式\) 之前呼叫物件的解構函式。  
  
 如果 **delete** 運算子的運算元是可修改的左值，其值在刪除物件之後為未定義。  
  
## 使用 delete  
 [delete 運算子](../cpp/delete-operator-cpp.md)有兩種語法變化：一種用於單一物件，另一種用於物件陣列。  下列程式碼片段示範兩者不同之處：  
  
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
  
 下列兩種情況會產生未定義的結果：對物件使用陣列形式的刪除 \(delete \[ \]\)，以及對陣列使用非陣列形式的刪除。  
  
## 範例  
 如需使用 **delete** 的範例，請參閱 [new 運算子](../cpp/new-operator-cpp.md)。  
  
## delete 運作方式  
 [delete 運算子](../cpp/delete-operator-cpp.md)會叫用 [operator delete](../misc/operator-delete-function.md) 函式。  
  
 對於不是類別類型 \([class](../cpp/class-cpp.md)、[struct](../cpp/struct-cpp.md) 或 [union](../cpp/unions.md)\) 的物件，會叫用全域 delete 運算子。  對於類別類型的物件，如果刪除運算式是以一元範圍解析運算子 \(::\) 開頭，則會在全域範圍中解析解除配置函式的名稱。  否則，如果指標不是 Null，delete 運算子會在解除配置記憶體之前叫用物件的解構函式。  delete 運算子可以依類別來定義；如果指定類別沒有這類定義，會叫用全域 delete 運算子。  如果使用刪除運算式來解除配置靜態類型包含虛擬解構函式的類別物件，則會透過該物件之動態類型的虛擬解構函式來解析解除配置函式。  
  
## 請參閱  
 [具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [new 和 delete 運算子](../cpp/new-and-delete-operators.md)   
 [operator delete 函式](../misc/operator-delete-function.md)