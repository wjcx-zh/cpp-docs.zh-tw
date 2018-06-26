---
title: C + + 視窗物件和 HWND 之間的關聯性 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- HWND
dev_langs:
- C++
helpviewer_keywords:
- Windows window [MFC]
- window objects [MFC], HWND and
- HWND [MFC]
- CWnd class [MFC], HWND
- HWND, window objects [MFC]
ms.assetid: f2e76340-6691-4ee6-9424-0345634a9469
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3864de8b3133fd2284b3ce57b75b30d8f41c26a7
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928524"
---
# <a name="relationship-between-a-c-window-object-and-an-hwnd"></a>C++ 視窗物件和 HWND 之間的關聯性
視窗*物件*是 c + + 物件`CWnd`類別 （或衍生的類別），程式會直接建立。 它會移，而則是放在程式的建構函式和解構函式呼叫的回應。 Windows*視窗*，相反地，就會對應到視窗，並會耗用系統資源，當其存在時的內部 Windows 資料結構的不透明控制代碼。 Windows 視窗由 「 視窗控制代碼 」 (`HWND`) 和之後，會建立`CWnd`物件由呼叫`Create`類別成員函式`CWnd`。 呼叫程式或使用者的動作，可能會終結視窗。 視窗控制代碼會儲存在視窗物件的*m_hWnd*成員變數。 下圖顯示 c + + 視窗物件和 Windows 視窗之間的關聯性。 建立視窗中會討論[建立 Windows](../mfc/creating-windows.md)。 終結視窗中會討論[終結視窗物件](../mfc/destroying-window-objects.md)。  
  
 ![CWnd 視窗物件和結果視窗](../mfc/media/vc37fj1.gif "vc37fj1")  
視窗物件和 Windows 視窗  
  
## <a name="see-also"></a>另請參閱  
 [視窗物件](../mfc/window-objects.md)

