---
title: Naked (C)
ms.date: 11/04/2016
helpviewer_keywords:
- naked keyword [C], storage-class attribute
- naked keyword [C]
- prolog code
- epilog code
ms.assetid: 23b1209b-93ba-46ad-a60f-2327c1933eaf
ms.openlocfilehash: 519d7bceb700e9862f0d0025b755cf28fb0fbc0c
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149774"
---
# <a name="naked-c"></a>Naked (C)

**Microsoft 專屬**

naked 儲存類別屬性是 Microsoft 專有的 C 語言擴充功能。 編譯器會針對以 naked 儲存類別屬性宣告的函式，產生不具初構和終解程式碼的程式碼。 當您需要使用內嵌組合語言程式碼撰寫自己的初構/終解程式碼序列時，naked 函式會很有用。 naked 函式在撰寫虛擬裝置驅動程式方面也很實用。

如需使用 naked 屬性的特定資訊，請參閱 [Naked 函式](../c-language/naked-functions.md)。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[C 擴充的儲存類別屬性](../c-language/c-extended-storage-class-attributes.md)
