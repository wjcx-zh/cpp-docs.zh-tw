---
title: 一般視窗建立順序
ms.date: 11/04/2016
helpviewer_keywords:
- sequence [MFC], window creation
- frame windows [MFC], creating
- windows [MFC], creating
- sequence [MFC]
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
ms.openlocfilehash: 0b09543d659448454bbc7c2cca6abee5de3013e5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618747"
---
# <a name="general-window-creation-sequence"></a>一般視窗建立順序

當您建立自己的視窗（例如子視窗）時，此架構所使用的程式與[建立檔/視圖](document-view-creation.md)時所述的進程大致相同。

MFC 提供的所有視窗類別都採用[兩階段式的結構](one-stage-and-two-stage-construction-of-objects.md)。 也就是說，在 c + + **new**運算子的調用期間，此函式會配置並初始化 c + + 物件，但不會建立對應的 Windows 視窗。 這是藉由呼叫 window 物件的[Create](reference/cwnd-class.md#create)成員函式來完成。

成員函式 `Create` 會建立 Windows 視窗，並將其儲存 `HWND` 在 c + + 物件的公用資料成員[m_hWnd](reference/cwnd-class.md#m_hwnd)。 `Create`提供建立參數的完整彈性。 在呼叫之前 `Create` ，您可能會想要使用全域函式[AfxRegisterWndClass](reference/application-information-and-management.md#afxregisterwndclass)來註冊視窗類別，以便設定框架的圖示和類別樣式。

針對框架視窗，您可以使用[LoadFrame](reference/cframewnd-class.md#loadframe)成員函式，而不是 `Create` 。 `LoadFrame`讓 Windows 視窗使用較少的參數。 它會從資源取得許多預設值，包括框架的標題、圖示、快速鍵對應表和功能表。

> [!NOTE]
> 您的圖示、快速鍵對應表和功能表資源必須擁有一般資源識別碼（例如**IDR_MAINFRAME**），LoadFrame 才會載入它們。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [視窗物件](window-objects.md)

- [註冊視窗「類別」](registering-window-classes.md)

- [終結視窗物件](destroying-window-objects.md)

- [建立檔框架視窗](creating-document-frame-windows.md)

## <a name="see-also"></a>另請參閱

[建立視窗](creating-windows.md)
