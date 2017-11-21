---
title: "靜態成員 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
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
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cb2597352fcc4a263dc2ceb93121a95dcd493f44
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="static-members-c"></a>靜態成員 (C++)
類別可以包含靜態資料成員和成員函式。 當資料成員宣告為**靜態**，只能有一個複本的資料會保留類別的所有物件。
  
 靜態資料成員不是特定類別類型之物件的一部分。 因此，靜態資料成員的宣告不視為定義。 資料成員是在類別範圍中宣告的，不過，定義是在檔案範圍執行。 這些靜態成員具有外部連結。 下面這個範例可說明這點：  
  
```  
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
  
```  
long nBytes = BufferedOutput::bytecount;  
```  
  
 若要靜態成員存在，不需要有類別類型的物件存在。 靜態成員也可以存取使用成員選取 (**。** 和 **->** ) 運算子。 例如:   
  
```  
BufferedOutput Console;  
  
long nBytes = Console.bytecount;  
```  
  
 在上述情況中，不會評估物件 (`Console`) 的參考；傳回值是靜態物件 `bytecount` 的傳回值。  
  
 靜態資料成員是受類別成員存取規則規範，因此，只有類別成員函式和 friend 才能進行靜態資料成員的私用存取。 這些規則所述[成員存取控制](../cpp/member-access-control-cpp.md)。 例外狀況是不管其存取限制，靜態資料成員必須在檔案範圍中定義。 如果資料成員將明確初始化，定義中必須提供初始設定式。  
  
 靜態成員的類型未以類別名稱限定。 因此，`BufferedOutput::bytecount` 的類型是 `long`。  
  
## <a name="see-also"></a>另請參閱  
 [類別和結構](../cpp/classes-and-structs-cpp.md)