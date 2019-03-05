---
title: 使用者按鈕處理常式
ms.date: 11/04/2016
f1_keywords:
- ON_BN_HILITE
- ON_BN_DOUBLECLICKED
- ON_BN_CLICKED
- ON_BN_PAINT
- ON_BN_DISABLE
- ON_BN_UNHILITE
helpviewer_keywords:
- ON_BN_PAINT
- user buttons [MFC]
- ON_BN_DOUBLECLICKED [MFC]
- ON_BN_DISABLE [MFC]
- ON_BN_UNHILITE [MFC]
- ON_BN_HILITE [MFC]
- ON_BN_CLICKED [MFC]
ms.assetid: 410ea968-478f-4806-b7b8-5d7c8dc2bf42
ms.openlocfilehash: 1b79c781243b0af02479d37865a86577311789da
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263438"
---
# <a name="user-button-handlers"></a>使用者按鈕處理常式

下列的對應項目會對應至函式原型。

|對應項目|函式原型|
|---------------|------------------------|
|ON_BN_CLICKED( \<id>, \<memberFxn> )|afx_msg void memberFxn( );|
|ON_BN_DISABLE( \<id>, \<memberFxn> )|afx_msg void memberFxn( );|
|ON_BN_DOUBLECLICKED( \<id>, \<memberFxn> )|afx_msg void memberFxn( );|
|ON_BN_HILITE( \<id>, \<memberFxn> )|afx_msg void memberFxn( );|
|ON_BN_PAINT( \<id>, \<memberFxn> )|afx_msg void memberFxn( );|
|ON_BN_UNHILITE( \<id>, \<memberFxn> )|afx_msg void memberFxn( );|

## <a name="see-also"></a>另請參閱

[訊息對應](../../mfc/reference/message-maps-mfc.md)
