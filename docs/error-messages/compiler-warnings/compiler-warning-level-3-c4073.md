---
title: "編譯器警告 (層級 3) C4073 | Microsoft Docs"
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
  - "C4073"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4073"
ms.assetid: 50081a6e-6acd-45ff-8484-9b1ea926cc5c
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 3) C4073
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

初始設定式置於程式庫初始化區域  
  
 僅協力廠商程式庫開發人員得以使用此程式庫初始化區域，其由 [\#pragma init\_seg](../../preprocessor/init-seg.md) 所指定。  下列範例會產生 C4073：  
  
```  
// C4073.cpp  
// compile with: /W3  
#pragma init_seg(lib)   // C4073  
  
// try this line to resolve the warning  
// #pragma init_seg(user)  
  
int main() {  
}  
```