---
title: MSG 結構 1 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- MSG
dev_langs:
- C++
helpviewer_keywords:
- MSG structure [MFC]
ms.assetid: dc166d27-9423-41f1-9599-5ba76d2f0138
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2819faa25e2dbd41d6578d60780d13011bb645c0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388390"
---
# <a name="msg-structure1"></a>MSG 結構 1

`MSG`結構包含來自執行緒之訊息佇列的訊息資訊。

## <a name="syntax"></a>語法

```
typedef struct tagMSG {     // msg
    HWND hwnd;
    UINT message;
    WPARAM wParam;
    LPARAM lParam;
    DWORD time;
    POINT pt;
} MSG;
```

#### <a name="parameters"></a>參數

*hwnd*<br/>
識別的視窗的視窗程序接收訊息。

*message*<br/>
指定的訊息編號。

*wParam*<br/>
指定訊息的其他資訊。 確切意義取決於值`message`成員。

*lParam*<br/>
指定訊息的其他資訊。 確切意義取決於值`message`成員。

*time*<br/>
指定公佈訊息的時間。

*太平洋時間*<br/>
公佈訊息時，請指定資料指標位置，以螢幕座標表示。

## <a name="requirements"></a>需求

**標頭：** winuser.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

