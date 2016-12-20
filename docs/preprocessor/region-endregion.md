---
title: "region、endregion | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.endregion"
  - "endregion_CPP"
  - "region_CPP"
  - "vc-pragma.region"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "endregion pragma"
  - "Pragma, endregion"
  - "Pragma, 區域"
  - "region pragma"
ms.assetid: c697f807-622f-4796-851b-68a42bbecd84
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# region、endregion
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**\#pragma region** 可讓您指定程式碼區塊，當您使用 Visual Studio 程式碼編輯器的[大綱功能](../Topic/Outlining.md)時，可以展開或摺疊該程式碼區塊。  
  
## 語法  
  
```  
#pragma region name  
#pragma endregion comment  
```  
  
#### 參數  
 `comment` \(選擇性\)  
 會顯示在程式碼編輯器中的註解。  
  
 *name*\(選擇性\)  
 區域的名稱。此名稱會顯示在程式碼編輯器中。  
  
## 備註  
 **\#pragma endregion** 會標記 **\#pragma region** 區塊的結尾。  
  
 `#region` 區塊必須以 **\#pragma endregion** 結束。  
  
## 範例  
  
```  
// pragma_directives_region.cpp  
#pragma region Region_1  
void Test() {}  
void Test2() {}  
void Test3() {}  
#pragma endregion Region_1  
  
int main() {}  
```  
  
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)