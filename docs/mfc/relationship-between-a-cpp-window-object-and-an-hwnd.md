---
title: "C + + 視窗物件和 HWND 之間的關聯性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: HWND
dev_langs: C++
helpviewer_keywords:
- Windows window [MFC]
- window objects [MFC], HWND and
- HWND [MFC]
- CWnd class [MFC], HWND
- HWND, window objects [MFC]
ms.assetid: f2e76340-6691-4ee6-9424-0345634a9469
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b441077de3a81de569627b6d7acf7cee8ca17b33
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="relationship-between-a-c-window-object-and-an-hwnd"></a>C++ 視窗物件和 HWND 之間的關聯性
視窗*物件*是 c + + 物件`CWnd`類別 （或衍生的類別），程式會直接建立。 它會移，而則是放在程式的建構函式和解構函式呼叫的回應。 Windows*視窗*，相反地，就會對應到視窗，並會耗用系統資源，當其存在時的內部 Windows 資料結構的不透明控制代碼。 Windows 視窗由 「 視窗控制代碼 」 (`HWND`) 和之後，會建立`CWnd`物件由呼叫**建立**類別成員函式`CWnd`。 呼叫程式或使用者的動作，可能會終結視窗。 視窗控制代碼會儲存在視窗物件的`m_hWnd`成員變數。 下圖顯示 c + + 視窗物件和 Windows 視窗之間的關聯性。 建立視窗中會討論[建立 Windows](../mfc/creating-windows.md)。 終結視窗中會討論[終結視窗物件](../mfc/destroying-window-objects.md)。  
  
 ![CWnd 視窗物件和結果視窗](../mfc/media/vc37fj1.gif "vc37fj1")  
視窗物件和 Windows 視窗  
  
## <a name="see-also"></a>請參閱  
 [視窗物件](../mfc/window-objects.md)

