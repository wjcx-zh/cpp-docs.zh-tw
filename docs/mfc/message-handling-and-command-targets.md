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
ms.openlocfilehash: f9212e32605a1fed179c931d4f63833e17870b5c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442532"
---
# <a name="message-handling-and-command-targets"></a>訊息處理和命令目標

命令分派介面`IOleCommandTarget`定義一個簡單且可擴充的機制，來查詢和執行命令。 這項機制會比使用自動化的`IDispatch`因為它會完全依賴一組標準的命令; 命令很少會具有引數，並牽涉到任何型別資訊 （型別安全就會受到影響的命令引數）。

在命令分派介面設計中，每個命令會屬於 「 命令群組 」 本身識別與**GUID**。 因此，任何人都可以定義新的群組，並定義而不需要與 Microsoft 協調或任何其他廠商的該群組內的所有命令。 (這是本質上定義的相同方法**dispinterface**加上**Dispid**在自動化中。 沒有重疊，雖然這個命令的路由機制僅適用於命令路由，不能用於指令碼/可程式性大規模自動化控制代碼的形式）。

`IOleCommandTarget` 處理下列案例：

- 當物件是就地啟用，只有通常會顯示物件的工具列，而且物件的工具列可能有一些類似的容器命令的按鈕**列印**，**預覽列印**， **儲存**，**新增**，**縮放**，和其他人。 （標準建議物件移除就地啟用這類按鈕從工具列，或在至少停用它們。 此設計可讓這些命令來啟用，而且尚未路由傳送至正確的處理常式。）目前沒有任何機制可用於將這些命令分派給容器的物件。

- 當主動式文件內嵌在主動式文件容器 （例如 Office Binder) 時，容器可能需要將命令傳送這類**列印**，**版面**，**屬性**，並可包含的使用中文件的其他項目。

這個簡單的命令路由無法透過現有的自動化標準來處理和`IDispatch`。 不過，額外負荷涉及`IDispatch`多超出所需的因此`IOleCommandTarget`提供一個簡單的方法，來達到相同的結束：

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

`QueryStatus`以下方法會測試是否一組特定的命令，以識別集合**GUID**，支援。 這個呼叫會填滿陣列**OLECMD**值 （結構） 支援的命令，以及傳回文字描述命令和/或狀態資訊的名稱清單。 當呼叫端想要叫用命令時，它可以傳遞命令 (和集合**GUID**) 來`Exec`選項和引數，以及取回傳回的值。

## <a name="see-also"></a>另請參閱

[主動式文件容器](../mfc/active-document-containers.md)

