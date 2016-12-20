---
title: "Setting Up a Static Link to the Registrar Code (C++ Only) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "連結 [C++], to ATL Registrar code"
  - "statically linking to ATL Registrar code"
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Setting Up a Static Link to the Registrar Code (C++ Only)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 用戶端可以建立一個靜態連結管理員的程式碼。  靜態連接管理員的剖析器會增加大約 5K 至發行組建。  
  
 最簡單的方式來設定靜態連接會假設您在物件的宣告指定 [DECLARE\_REGISTRY\_RESOURCEID](../Topic/DECLARE_REGISTRY_RESOURCEID.md) 。  \(這是 ATL 所使用的預設規格\)。  
  
### 使用 DECLARE\_REGISTRY\_RESOURCEID，建立一個使用靜態連結。  
  
1.  指定 [\/D](../build/reference/d-preprocessor-definitions.md)`_ATL_STATIC_REGISTRY` 而不是\/D**\_ATL\_DLL**。  
  
2.  請重新編譯。  
  
## 請參閱  
 [登錄元件 \(登錄器\)](../atl/atl-registry-component-registrar.md)