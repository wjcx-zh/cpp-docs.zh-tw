---
title: "編譯器錯誤 C3873 | Microsoft Docs"
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
  - "C3873"
helpviewer_keywords: 
  - "C3873"
ms.assetid: e68fd3be-2391-492b-ac3f-d2428901b2e9
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3873
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'char'：識別項的第一個字元不可以是這個字元  
  
 C\+\+ 編譯器會遵循 C\+\+11 標準處理識別項中允許的字元。 識別項中只允許特定範圍的字元和通用字元名稱。 其他限制也適用於識別項的起始字元。 如需詳細資訊及允許的字元和通用字元名稱範圍清單，請參閱 [C\+\+ 識別項](../../cpp/identifiers-cpp.md)。  
  
 編譯 C\+\+\/CLI 程式碼時，識別項中允許之字元範圍的限制較少。 使用 \/clr 編譯之程式碼中的識別項應該遵循[標準 ECMA\-335：通用語言基礎結構 \(CLI\)](http://www.ecma-international.org/publications/standards/Ecma-335.htm)。  
  
 下列範例會產生 C3873：  
  
```  
// C3873.cpp int main() { int \u036F_abc;   // C3873, not in allowed range for initial character int abc_\u036F;   // OK, in allowed range for non-initial character }  
```