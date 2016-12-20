---
title: "靜態成員 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "類別執行個體 [C++], 共用成員"
  - "類別執行個體 [C++], 靜態成員"
  - "類別成員 [C++], 共用"
  - "類別成員 [C++], static"
  - "資料成員 [C++], 靜態資料成員"
  - "執行個體建構函式, 共用成員"
  - "執行個體建構函式, 靜態成員"
  - "成員 [C++], 靜態資料成員"
  - "靜態資料成員 [C++]"
  - "靜態成員 [C++], 資料成員"
ms.assetid: 9cc8cf0f-d74c-46f2-8e83-42d4e42c8370
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 靜態成員 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

類別可以包含靜態資料成員和成員函式。  當資料成員宣告為 **static** 時，只維護該類別所有物件的一份資料複本   \(如需詳細資訊，請參閱[靜態成員函式](../misc/static-member-functions.md)\)。  
  
 靜態資料成員不是特定類別類型之物件的一部分。  因此，靜態資料成員的宣告不視為定義。  資料成員是在類別範圍中宣告的，不過，定義是在檔案範圍執行。  這些靜態成員具有外部連結。  下面這個範例可說明這點：  
  
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
  
 靜態資料成員可以在不參考類別類型物件的情況下參考。  使用 `BufferedOutput` 物件撰寫的位元組數目可以如下取得：  
  
```  
long nBytes = BufferedOutput::bytecount;  
```  
  
 若要靜態成員存在，不需要有類別類型的物件存在。  靜態成員也可以透過成員選取 \(**.** 和 **–\>**\) 運算子存取。  例如:  
  
```  
BufferedOutput Console;  
  
long nBytes = Console.bytecount;  
```  
  
 在上述情況中，不會評估物件 \(`Console`\) 的參考；傳回值是靜態物件 `bytecount` 的傳回值。  
  
 靜態資料成員是受類別成員存取規則規範，因此，只有類別成員函式和 friend 才能進行靜態資料成員的私用存取。  這些規則會在[成員存取控制項](../cpp/member-access-control-cpp.md)中加以說明。  例外狀況是不管其存取限制，靜態資料成員必須在檔案範圍中定義。  如果資料成員將明確初始化，定義中必須提供初始設定式。  
  
 靜態成員的類型未以類別名稱限定。  因此，`BufferedOutput::bytecount` 的類型是 `long`。  
  
## 請參閱  
 [類別和結構](../cpp/classes-and-structs-cpp.md)