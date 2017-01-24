---
title: "編譯器警告 (層級 1) C4691 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4691"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4691"
ms.assetid: 722133d9-87f6-46c1-9e86-9825453d6999
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4691
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' : 所參考的型別應該是在未參考的 assembly 'file' 中，已用目前轉譯單位中定義的型別取代  
  
 中繼資料檔案包含未參考的原始型別定義，而編譯器是使用區域型別定義。  
  
 在您重建 *file* 的情形下，可以忽略 C4691，或是透過 pragma  [warning](../../preprocessor/warning.md) 加以關閉。也就是說，如果您在建置的檔案是與編譯器必須尋找型別定義的檔案相同，您可以忽略 C4691。  
  
 但是，如果編譯器使用的定義不是來自中繼資料所參考的同一個組件，可能會發生未預期的行為；CLR 型別不但是由型別名稱定型別，而且也由組件定型別。也就是說，組件 z.dll 的型別 Z 與組件 y.dll 的型別 Z 是不同的。  
  
## 範例  
 下列範例包含原始的型別定義。  
  
```  
// C4691_a.cpp  
// compile with: /clr /LD /W1  
public ref class Original_Type {};  
```  
  
## 範例  
 下列範例參考 C4691\_a.dll，並宣告型別 Original\_Type 的欄位。  
  
```  
// C4691_b.cpp  
// compile with: /clr /LD  
#using "C4691_a.dll"  
public ref class Client {  
public:  
   Original_Type^ ot;  
};  
```  
  
## 範例  
 下列範例會產生 C4691。請注意，此範例包含 Original\_Type 的定義，而並不參考 C4691a.dll。  
  
 若要解決這個問題，請參考包含原始型別定義的中繼資料檔，並移除區域宣告和定義。  
  
```  
// C4691_c.cpp  
// compile with: /clr /LD /W1  
// C4691 expected  
  
// Uncomment the following line to resolve.  
// #using "C4691_a.dll"  
#using "C4691_b.dll"  
  
// Delete the following line to resolve.  
ref class Original_Type;  
  
public ref class MyClass : Client {};  
```