---
title: "訊息處理和命令目標 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IOleCommandTarget
dev_langs: C++
helpviewer_keywords:
- command targets [MFC]
- message handling [MFC], active documents
- IOleCommandTarget interface [MFC]
- command routing [MFC], command targets
ms.assetid: e45ce14c-e6b6-4262-8f3b-4e891e0ec2a3
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 81ec1f2a1f419715a3e8e9fbac2fcba3c7584a9b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="message-handling-and-command-targets"></a>訊息處理和命令目標
命令分派介面`IOleCommandTarget`定義一個簡單且可延伸機制，來查詢及執行命令。 這項機制會比自動化的簡單`IDispatch`因為它會完全依賴一組標準的命令; 命令很少需要引數，並不涉及任何類型資訊 （型別安全就會受到影響的命令引數）。  
  
 在命令分派介面的設計，每個命令都屬於 「 命令群組 」 本身識別與**GUID**。 因此，任何人都可以定義新的群組，並定義而不需要任何需要與 Microsoft 協調或任何其他廠商的該群組內的所有命令。 (這是基本上相同的方式為定義的**dispinterface**加上**Dispid**自動化中。 沒有重疊，雖然此命令路由機制，是只用於命令傳送並不適用於指令碼/可程式性在大規模自動化控制代碼的形式）。  
  
 `IOleCommandTarget`處理下列案例：  
  
-   使用物件時就地啟用，通常會顯示物件的工具列和物件的工具列可能有對於某些像容器命令的按鈕**列印**，**預覽列印**， **儲存**， `New`，**縮放**，和其他人。 （標準建議的物件移除就地啟用這類按鈕的工具列中，或至少停用。 此設計可讓這些命令會啟用，而且傳送到正確的處理常式。）目前沒有任何機制來分派這些命令的容器物件。  
  
-   當主動式文件內嵌在主動式文件容器 （例如 Office Binder) 中時，容器可能要將命令傳送這類**列印**，**版面**，**屬性**，和其他人所包含的主動式文件。  
  
 無法處理這個簡單的命令路由到現有的自動化標準和`IDispatch`。 不過，額外負荷涉及`IDispatch`過高而無須在這裡，因此`IOleCommandTarget`提供簡單的方式來達成相同的端點：  
  
```  
interface IOleCommandTarget : IUnknown  
    {  
    HRESULT QueryStatus(  
        [in] GUID *pguidCmdGroup,  
        [in] ULONG cCmds,  
        [in,out][size_is(cCmds)] OLECMD *prgCmds,  
        [in,out] OLECMDTEXT *pCmdText);  
    HRESULT Exec(  
        [in] GUID *pguidCmdGroup,  
        [in] DWORD nCmdID,  
        [in] DWORD nCmdExecOpt,  
        [in] VARIANTARG *pvaIn,  
        [in,out] VARIANTARG *pvaOut);  
    }  
```  
  
 `QueryStatus`以下方法會測試是否識別具有集合了一組特定的命令， **GUID**，支援。 此呼叫將填入陣列**OLECMD**值 （結構） 具有支援的命令，以及傳回文字，描述命令和/或狀態資訊的名稱清單。 當呼叫端想要叫用命令時，它可以傳遞的命令 (和組**GUID**) 至**Exec**選項和引數，以及取得傳回值。  
  
## <a name="see-also"></a>請參閱  
 [主動式文件容器](../mfc/active-document-containers.md)

