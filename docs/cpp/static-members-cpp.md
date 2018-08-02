---
title: 靜態成員 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- class members [C++], static
- instance constructors, static members
- class members [C++], shared
- members [C++], static data members
- static members [C++], data members
- static data members [C++]
- data members [C++], static data members
- class instances [C++], shared members
- instance constructors, shared members
- class instances [C++], static members
ms.assetid: 9cc8cf0f-d74c-46f2-8e83-42d4e42c8370
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2d202e48bbcd09c3f4071af21e942cb1353f7a6b
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466237"
---
# <a name="static-members-c"></a>靜態成員 (C++)
類別可以包含靜態資料成員和成員函式。 當資料成員宣告為**靜態**，只有一份資料會保留類別的所有物件。
  
 靜態資料成員不是特定類別類型之物件的一部分。 因此，靜態資料成員的宣告不視為定義。 資料成員是在類別範圍中宣告的，不過，定義是在檔案範圍執行。 這些靜態成員具有外部連結。 下面這個範例可說明這點：  
  
```cpp  
// static_data_members.cpp  
class BufferedOutput  
{  
public:  
   // Return number of bytes written by any object of this class.  
   short BytesWritten()  
   {  
      return bytecount;  
   }  
  
   // Reset the counter.  
   static void ResetCount()  
   {  
      bytecount = 0;  
   }  
  
   // Static member declaration.  
   static long bytecount;  
};  
  
// Define bytecount in file scope.  
long BufferedOutput::bytecount;  
  
int main()  
{  
}  
```  
  
 在上述程式碼中，成員 `bytecount` 是在類別 `BufferedOutput` 中宣告，但必須在類別宣告之外加以定義。  
  
 靜態資料成員可以在不參考類別類型物件的情況下參考。 使用 `BufferedOutput` 物件撰寫的位元組數目可以如下取得：  
  
```cpp  
long nBytes = BufferedOutput::bytecount;  
```  
  
 若要靜態成員存在，不需要有類別類型的物件存在。 靜態成員也可以存取使用成員選取 (**。** 並**->**) 運算子。 例如:   
  
```cpp  
BufferedOutput Console;  
  
long nBytes = Console.bytecount;  
```  
  
 在上述情況中，不會評估物件 (`Console`) 的參考；傳回值是靜態物件 `bytecount` 的傳回值。  
  
 靜態資料成員是受類別成員存取規則規範，因此，只有類別成員函式和 friend 才能進行靜態資料成員的私用存取。 這些規則所述[成員存取控制](../cpp/member-access-control-cpp.md)。 例外狀況是不管其存取限制，靜態資料成員必須在檔案範圍中定義。 如果資料成員將明確初始化，定義中必須提供初始設定式。  
  
 靜態成員的類型未以類別名稱限定。 因此，該類`BufferedOutput::bytecount`已**長**。  
  
## <a name="see-also"></a>另請參閱  
 [類別和結構](../cpp/classes-and-structs-cpp.md)