---
title: "標準命令和視窗 ID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "標準命令和視窗 ID"
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# 標準命令和視窗 ID
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MFC 程式庫定義在 Afxres.h 的標準命令和視窗 ID。  這些 ID 在資源編輯器和屬性視窗內最常用來將訊息加入至處理函式。  所有標準命令具有 **ID\_** 前置詞。  例如，當您使用功能表編輯器時，您通常要繫結檔案開啟功能表項目至標準 `ID_FILE_OPEN` 命令 ID.  
  
 對於大部分的標準命令，應用程式程式碼不需要參考命令 ID，，因為這個架構會在其主框架類別 \(`CWinThread`、 `CWinApp`、 `CView`， **CDocument**的訊息對應處理命令，依此類推\)。  
  
 除了標準命令 ID 之外，還有 **AFX\_ID**前置的一些其他標準 ID 的定義。  這些 ID 包含標準視窗 ID 前置詞 \( **AFX\_IDW\_**\)、字串 ID 前置詞 \( **AFX\_IDS\_**\) 和數個其他型別。  
  
 從 **AFX\_ID** 前置詞開頭程式設計人員，不過，您最少使用的 ID 可能需要參考來參考 **AFX\_ID** 的這些 ID，覆寫框架上運作。  
  
 ID 在此參考沒有個別文件。  您可以找出其詳細資訊在技術提示 [20](../../mfc/tn020-id-naming-and-numbering-conventions.md)、 [21](../../mfc/tn021-command-and-message-routing.md)和 [22](../../mfc/tn022-standard-commands-implementation.md)。  
  
> [!NOTE]
>  標頭檔 Afxres.h 間接包含在 Afxwin.h 。  在應用程式的資源指令碼 \(.rc\) 檔必須明確包含下列陳述式：  
  
 [!code-cpp[NVC_MFC_Utilities#47](../../mfc/codesnippet/CPP/standard-command-and-window-ids_1.h)]  
  
## 請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)