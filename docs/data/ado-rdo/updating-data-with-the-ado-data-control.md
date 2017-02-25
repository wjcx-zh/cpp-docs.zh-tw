---
title: "以 ADO 資料控制項更新資料 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ADO [C++], 資料繫結"
  - "ADO [C++], 資料控制項"
ms.assetid: 8bec34b9-93dd-4872-b023-55ac011ccff5
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 以 ADO 資料控制項更新資料
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ADO 資料控制項資料可為唯讀或可修改。  
  
### 若要建立使用 ADO 資料控制項來修改資料的應用程式  
  
1.  設定 ADO 資料控制項的 **CursorLocation** 屬性。  選項包括：  
  
    -   伺服器端  
  
    -   用戶端  
  
2.  設定 ADO 資料控制項的 **LockType** 屬性。  建議使用開放式並行存取。  
  
3.  設定 ADO 資料控制項的 **CursorType** 屬性。  選項包括：  
  
    -   索引鍵集 \(Keyset\) 指標  
  
    -   動態資料指標  
  
    -   靜態資料指標  
  
     請確認 OLE DB 提供者 \(Provider\) 可支援選定選項。  
  
4.  視需要設定資料繫結控制項的屬性，以允許可更新性。  請注意，某些控制項並不允許更新。  
  
 如需這些屬性的詳細資訊，請參閱 ADO 文件。  
  
## 請參閱  
 [ADO 資料繫結](../../data/ado-rdo/ado-databinding.md)   
 [在 Visual C\+\+ 中使用 ADO 資料繫結](../../data/ado-rdo/using-ado-databinding-in-visual-cpp.md)