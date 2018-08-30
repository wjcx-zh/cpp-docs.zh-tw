---
title: C 語言 api 的關聯性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.mfc
dev_langs:
- C++
helpviewer_keywords:
- books [MFC], about MFC and Windows SDK
- books [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- Windows API [MFC], and MFC
ms.assetid: 334e8efc-f3cc-4018-bc2e-02908b2a39fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d0bb7aa4f647ceeb61c20cccd626d9da999b241
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200108"
---
# <a name="relationship-to-the-c-language-api"></a>與 C 語言應用程式開發介面的關聯性
區隔 MFC 程式庫與其他 Windows 類別程式庫的單一特點是，其與以 C 語言撰寫的 Windows API 的對應非常接近。 此外，您通常可以自由地混合對類別庫的呼叫與直接對 Windows API 的呼叫。 然而，這種直接存取並不表示類別可以完整取代該 API。 開發人員必須偶爾還是會進行直接呼叫某些 Windows 函式，這類[SetCursor](/windows/desktop/api/winuser/nf-winuser-setcursor)並[GetSystemMetrics](https://msdn.microsoft.com/library/windows/desktop/ms724385)，例如。 只有在這麼做有明顯的好處時，才會由類別成員函式包裝 Windows 函式。  
  
 由於您有時必須呼叫原生 Windows 函式，因此您應該存取 C 語言 Windows API 文件。 這份文件隨附於 Microsoft Visual C++。  
  
> [!NOTE]
>  如需 MFC 程式庫架構的運作方式的概觀，請參閱 <<c0> [ 使用類別來撰寫應用程式的 Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)。  
  
## <a name="see-also"></a>另請參閱  
 [一般類別設計原理](../mfc/general-class-design-philosophy.md)
