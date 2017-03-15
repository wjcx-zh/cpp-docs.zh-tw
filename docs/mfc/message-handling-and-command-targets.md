---
title: "訊息處理和命令目標 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IOleCommandTarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令傳送, 命令目標"
  - "命令目標"
  - "IOleCommandTarget 介面"
  - "訊息處理, 主動式文件"
ms.assetid: e45ce14c-e6b6-4262-8f3b-4e891e0ec2a3
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 訊息處理和命令目標
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

命令分派介面 `IOleCommandTarget` 定義一個簡單的機制查詢並執行命令。  因為它完全依賴標準命令集，這個機制來自動化的 `IDispatch` 簡單;命令很少有引數，，和型別資訊不是包含的 \(型別安全為命令引數會降低\)。  
  
 在命令分派介面設計，每個命令所屬本身識別與 **GUID**的命令組」。  因此，任何在該群組中可以定義新的群組和定義任何命令，沒有任何需要配合 Microsoft 和其他廠商。\(這基本上是定義相同的方式就像 **dispinterface** 加上 Automation 的 **dispIDs** 。  有重疊在此處，不過，這個命令路由機制大型地只適用於命令路由和不做為指令碼\/可程式性當 Automation 控制代碼\)。  
  
 `IOleCommandTarget` 處理下列案例:  
  
-   當物件是就地啟動，，只有物件的工具列一般都是顯示和物件的工具列可能有特定的按鈕 \(例如 **Print**和 **Print** \[**預覽**\]， \[**儲存**\]、 \[**縮放**\]， `New`和其他的容器命令。\(就地啟用標準建議物件移除其工具列的這類按鈕或至少停用。  這種設計可以讓這些命令啟用，仍會傳送至正確的處理常式\)。目前，沒有物件的機制可以透過這些命令至容器。  
  
-   當現用文件在主動式文件容器內嵌 \(例如 Office 文件夾\)，容器可能需要傳送命令這類 **Print**和 **Page Setup**， \[**屬性**\] 和其他到包含現用文件。  
  
 這個簡單的命令路由可以透過現有的 Automation 標準和 `IDispatch`被處理。  不過，額外負荷與 `IDispatch` 所需的在這裡較多，因此， `IOleCommandTarget` 提供更簡單的方式達成相同目的:  
  
 `interface IOleCommandTarget : IUnknown`  
  
 `{`  
  
 `HRESULT QueryStatus(`  
  
 `[in] GUID *pguidCmdGroup,`  
  
 `[in] ULONG cCmds,`  
  
 `[in,out][size_is(cCmds)] OLECMD *prgCmds,`  
  
 `[in,out] OLECMDTEXT *pCmdText);`  
  
 `HRESULT Exec(`  
  
 `[in] GUID *pguidCmdGroup,`  
  
 `[in] DWORD nCmdID,`  
  
 `[in] DWORD nCmdExecOpt,`  
  
 `[in] VARIANTARG *pvaIn,`  
  
 `[in,out] VARIANTARG *pvaOut);`  
  
 `}`  
  
 這裡的 `QueryStatus` 方法會測試特定一組命令，以識別與 **GUID**的這個集合，是否支援。  這是呼叫命令支援的清單填入 **OLECMD** 值 \(結構\) 以及傳回描述命令和狀態資訊的名稱的文字。  當呼叫端想要叫用命令時，它可以透過命令 \(和集合 **GUID**\) 到 **Exec** 與選項和引數一起後面，取得傳回值。  
  
## 請參閱  
 [主動式文件容器](../mfc/active-document-containers.md)