---
title: 一般視窗建立順序
ms.date: 11/04/2016
helpviewer_keywords:
- sequence [MFC], window creation
- frame windows [MFC], creating
- windows [MFC], creating
- sequence [MFC]
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
ms.openlocfilehash: fb10ced78e230316a6e2982f24c1fb6e2e52ed8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364276"
---
# <a name="general-window-creation-sequence"></a>一般視窗建立順序

當您創建自己的視窗(如子視窗)時,框架使用的過程與[文檔/視圖創建](../mfc/document-view-creation.md)中所述的過程大致相同。

MFC 提供的所有視窗類別來[採用兩階段結構](../mfc/one-stage-and-two-stage-construction-of-objects.md)。 也就是說,在調用C++**新**運算元期間,構造函數分配並初始化C++物件,但不會創建相應的 Windows 視窗。 之後,通過調用視窗物件的[「創建](../mfc/reference/cwnd-class.md#create)成員」函數來完成此操作。

成員`Create`函數使 Windows`HWND`視窗並將儲存在C++物件的公共資料成員[m_hWnd](../mfc/reference/cwnd-class.md#m_hwnd)。 `Create`對創建參數具有完全的靈活性。 在調用`Create`之前,您可能希望使用全域函數[AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass)註冊視窗類,以便為框架設置圖示和類樣式。

對框架視窗,可以使用[LoadFrame](../mfc/reference/cframewnd-class.md#loadframe)成員函`Create`數而不是 。 `LoadFrame`使用較少的參數使Windows視窗。 它從資源獲取許多預設值,包括框架的標題、圖示、快速鍵表和功能表。

> [!NOTE]
> 您的圖示、快速鍵表和功能表資源必須具有通用資源 ID(如**IDR_MAINFRAME,** 以便由 LoadFrame 載入它們。

## <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [視窗物件](../mfc/window-objects.md)

- [註冊視窗"類"](../mfc/registering-window-classes.md)

- [銷毀視窗物件](../mfc/destroying-window-objects.md)

- [建立文件框架視窗](../mfc/creating-document-frame-windows.md)

## <a name="see-also"></a>另請參閱

[建立視窗](../mfc/creating-windows.md)
