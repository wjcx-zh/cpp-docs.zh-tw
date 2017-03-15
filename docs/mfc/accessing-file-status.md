---
title: "存取檔案狀態 | Microsoft Docs"
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
  - "範例 [MFC], 檔案狀態"
  - "檔案狀態 [C++]"
  - "檔案 [C++], 存取"
  - "檔案 [C++], 狀態資訊"
  - "檔案的狀態"
ms.assetid: 1b8891d6-eb0f-4037-a837-4928fe595222
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 存取檔案狀態
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`CFile` 也支援取得檔案狀態，包括檔案是否存在，建立和修改日期和時間、邏輯大小和路徑。  
  
### 取得檔案的狀態  
  
1.  使用 [CFile](../mfc/reference/cfile-class.md) 類別來取得和設定檔案的相關資訊。  一個有用的應用程式是使用 `CFile` 靜態成員函式 **GetStatus** 判斷檔案是否存在。  如果指定的檔案不存在，**GetStatus** 傳回 0。  
  
 因此，您可以使用 **GetStatus** 的結果會決定使用 **CFile::modeCreate** 旗標，則開啟檔案，如下所示範例時:  
  
 [!code-cpp[NVC_MFCFiles#3](../mfc/codesnippet/CPP/accessing-file-status_1.cpp)]  
  
 如需相關資訊，請參閱[Serialization](../mfc/serialization-in-mfc.md)。  
  
## 請參閱  
 [檔案](../mfc/files-in-mfc.md)