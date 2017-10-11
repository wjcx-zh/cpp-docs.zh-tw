---
title: "左值參考宣告子： &amp; |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '&'
dev_langs:
- C++
helpviewer_keywords:
- reference operator
- '& operator [C++], reference operator'
ms.assetid: edf0513d-3dcc-4663-b276-1269795dda51
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 6aa0c0a18d77f685369681c0d0400ada6f879e9d
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="lvalue-reference-declarator-amp"></a>左值參考宣告子：&amp;
保存物件的位址，但語法上的行為與物件相似。  
  
## <a name="syntax"></a>語法  
  
```  
  
type-id & cast-expression  
```  
  
## <a name="remarks"></a>備註  
 您可以將左值參考當做物件的另一個名稱。 左值參考宣告包含選擇性的指定名稱清單加上參考宣告符號。 參考必須經過初始化，而且不能變更。  
  
 只要物件的位址可以轉換為指定的指標類型，則該物件也可轉換為類似的參考類型。 例如，只要物件的位址可以轉換成 `char *` 類型，該物件也可轉換成 `char &` 類型。  
  
 請勿混淆參考宣告與使用[傳址運算子](../cpp/address-of-operator-amp.md)。 當`&`*識別碼*前面加上型別，例如`int`或`char`，*識別碼*宣告為類型的參考。 當`&`*識別碼*前面沒有由型別，其用法即的傳址運算子。  
  
## <a name="example"></a>範例  
 下列範例示範宣告 `Person` 物件和該物件之參考的參考宣告子。 因為 `rFriend` 是 `myFriend` 的參考，無論更新哪一個變數都會變更同一個物件。  
  
```  
// reference_declarator.cpp  
// compile with: /EHsc  
// Demonstrates the reference declarator.  
#include <iostream>  
using namespace std;  
  
struct Person  
{  
    char* Name;  
    short Age;  
};  
  
int main()  
{  
   // Declare a Person object.  
   Person myFriend;  
  
   // Declare a reference to the Person object.  
   Person& rFriend = myFriend;  
  
   // Set the fields of the Person object.  
   // Updating either variable changes the same object.  
   myFriend.Name = "Bill";  
   rFriend.Age = 40;  
  
   // Print the fields of the Person object to the console.  
   cout << rFriend.Name << " is " << myFriend.Age << endl;  
}  
```  
  
```Output  
Bill is 40  
```  
  
## <a name="see-also"></a>另請參閱  
 [參考](../cpp/references-cpp.md)   
 [參考類型函式引數](../cpp/reference-type-function-arguments.md)   
 [參考類型函式傳回](../cpp/reference-type-function-returns.md)   
 [指標的參考](../cpp/references-to-pointers.md)
