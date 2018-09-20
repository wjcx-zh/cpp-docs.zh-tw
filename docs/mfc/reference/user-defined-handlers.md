---
title: 使用者定義的處理常式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.handlers
dev_langs:
- C++
helpviewer_keywords:
- ON_REGISTERED_MESSAGE macro [MFC]
- ON_MESSAGE macro [MFC]
- user-defined handlers [MFC]
ms.assetid: 99478294-bef0-4ba7-a369-25a6abdcdb62
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 50348d36badb955a14f15e30d846b052b297b4a1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442535"
---
# <a name="user-defined-handlers"></a>使用者定義的處理常式

下列的對應項目會對應至函式原型。

|對應項目|函式原型|
|---------------|------------------------|
|ON_MESSAGE (\<訊息 >， \<memberFxn >)|afx_msg LRESULT memberFxn （WPARAM，LPARAM）;|
|ON_REGISTERED_MESSAGE ( \<nMessageVariable >， \<memberFxn >)|afx_msg LRESULT memberFxn （WPARAM，LPARAM）;|
|ON_THREAD_MESSAGE (\<訊息 >， \<memberFxn >)|afx_msg void memberFxn （WPARAM，LPARAM）;|
|ON_REGISTERED_THREAD_MESSAGE ( \<nMessageVariable >， \<memberFxn >)|afx_msg void memberFxn （WPARAM，LPARAM）;|

## <a name="see-also"></a>另請參閱

[訊息對應](../../mfc/reference/message-maps-mfc.md)<br/>
[WM_ 訊息的處理常式](../../mfc/reference/handlers-for-wm-messages.md)

