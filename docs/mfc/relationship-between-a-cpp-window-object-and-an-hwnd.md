---
title: C++ 視窗物件和 HWND 之間的關聯性
ms.date: 11/19/2018
f1_keywords:
- HWND
helpviewer_keywords:
- Windows window [MFC]
- window objects [MFC], HWND and
- HWND [MFC]
- CWnd class [MFC], HWND
- HWND, window objects [MFC]
ms.assetid: f2e76340-6691-4ee6-9424-0345634a9469
ms.openlocfilehash: 8cf8856be7166768c507932184e257cf69b0eb35
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57305194"
---
# <a name="relationship-between-a-c-window-object-and-an-hwnd"></a>C++ 視窗物件和 HWND 之間的關聯性

視窗*物件*是 c + + 中的物件`CWnd`類別 （或衍生的類別），程式會直接建立。 它會出現，並會回應您的程式建構函式和解構函式呼叫。 Windows*視窗*，相反地，為內部的 Windows 資料結構，對應至視窗，並且會耗用系統資源時出現的不透明控制代碼。 Windows 視窗由 「 視窗控制代碼 」 (`HWND`) 和之後，會建立`CWnd`的呼叫所建立物件`Create`類別成員函式`CWnd`。 程式呼叫或使用者的動作，可能會終結視窗。 視窗控制代碼會儲存在視窗物件的*m_hWnd*成員變數。 下圖顯示 c + + 視窗物件 Windows 視窗之間的關聯性。 建立視窗中會討論[建立 Windows](../mfc/creating-windows.md)。 終結視窗中會討論[終結視窗物件](../mfc/destroying-window-objects.md)。

![CWnd 視窗物件和結果視窗](../mfc/media/vc37fj1.gif "CWnd 視窗物件和結果視窗") <br/>
視窗物件和 Windows 視窗

## <a name="see-also"></a>另請參閱

[視窗物件](../mfc/window-objects.md)
