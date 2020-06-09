---
title: 訊息處理和命令目標
ms.date: 11/04/2016
f1_keywords:
- IOleCommandTarget
helpviewer_keywords:
- command targets [MFC]
- message handling [MFC], active documents
- IOleCommandTarget interface [MFC]
- command routing [MFC], command targets
ms.assetid: e45ce14c-e6b6-4262-8f3b-4e891e0ec2a3
ms.openlocfilehash: cbcbce1e476fef0d076f9c25b46b3166c1eb5935
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624342"
---
# <a name="message-handling-and-command-targets"></a>訊息處理和命令目標

命令分派介面會 `IOleCommandTarget` 定義簡單且可擴充的機制來查詢和執行命令。 這項機制比 Automation 簡單， `IDispatch` 因為它完全依賴一組標準的命令; 命令很少會有引數，而且不會涉及任何類型資訊（命令引數的型別安全性也會降低）。

在命令分派介面設計中，每個命令都屬於一個以**GUID**識別的「命令群組」。 因此，任何人都可以定義新的群組，並定義該群組中的所有命令，而不需要與 Microsoft 或任何其他廠商協調。 （這基本上就是相同的定義方式，也**就是自動化**中的**dispid** 。 這裡有重迭，雖然此命令路由機制僅適用于命令路由，而不是用於大規模為自動化控制碼的腳本/程式設計。）

`IOleCommandTarget`會處理下列案例：

- 當物件就地啟用時，只會顯示物件的工具列，而且物件的工具列可能會有一些容器命令的按鈕，例如**列印**、**預覽列印**、**儲存**、**新增**、**縮放**等等。 （就地啟用標準建議物件從工具列移除這類按鈕，或至少停用它們。 這種設計可讓這些命令啟用，並路由傳送至正確的處理常式。）目前，沒有任何機制可讓物件將這些命令分派至容器。

- 當使用中的檔內嵌在活動文檔容器中（例如 Office 系結器）時，容器可能需要傳送命令（例如**列印**、版面**設定**、**屬性**和其他專案）到包含的現用檔。

這個簡單的命令路由可以透過現有的自動化標準和來處理 `IDispatch` 。 不過，所涉及的額外負荷在這裡需要的不只是 `IDispatch` ，因此 `IOleCommandTarget` 提供較簡單的方法來達到相同的結尾：

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

`QueryStatus`這裡的方法會測試是否支援一組特定的命令（以**GUID**識別的集合）。 此呼叫會以支援的命令清單填入**OLECMD**值（結構）陣列，以及傳回描述命令名稱和/或狀態資訊的文字。 當呼叫端想要叫用命令時，它可以將命令（和集**GUID**） `Exec` 連同選項和引數傳遞至，以取得傳回值。

## <a name="see-also"></a>另請參閱

[主動式文件容器](active-document-containers.md)
