---
title: "舊版作業系統上的 CImage 限制 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CImage
dev_langs: C++
helpviewer_keywords: CImage class [MFC], limitations
ms.assetid: 4bedaab8-7dd1-4c91-ab35-b75fb56765b0
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 27046704975bf8f5e28f12acbfa72e860660fdbd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cimage-limitations-with-earlier-operating-systems"></a>舊版作業系統上的 CImage 限制
許多 `CImage` 函式僅適用於較新版本的 Windows，如：Windows 95/98 或 Windows NT 4.0、Windows 2000。 本文說明某些方法的版本限制。  
  
 [Cimage:: Plgblt](../atl-mfc-shared/reference/cimage-class.md#plgblt)和[Maskblt](../atl-mfc-shared/reference/cimage-class.md#maskblt)只是 Windows NT 4.0 或更新版本。 它們在 Windows 95/98 或更新版本上執行的應用程式中無法運作。  
  
 [CImage::AlphaBlend](../atl-mfc-shared/reference/cimage-class.md#alphablend)和[Transparentblt](../atl-mfc-shared/reference/cimage-class.md#transparentblt)只有 Windows 2000 或更新版本以及 Windows 98 或更新版本，因為您必須與 msimg32.lib 連結才能使用這些方法。 (這個程式庫只有執行 Windows 2000 或更新版本以及 Windows 98 或更新版本的應用程式才能使用)。  
  
 您可以在 Windows 95 或 Windows NT 4.0 上執行的應用程式中包含 `AlphaBlend` 和 `TransparentBlt`，但是條件是只有這些方法絕對不會被呼叫。 如果您的應用程式包含這些方法，而且它必須在舊版作業系統上執行，您必須使用連結器的[/delayload](../build/reference/delayload-delay-load-import.md)來延遲 msimg32.lib 的載入。 只要您的應用程式在 Windows NT 4.0 或 Windows 95 下執行時不會呼叫這些方法之一，就不會嘗試載入 msimg32.lib。 您可以檢查透明度支援是否可以使用 `CImage::IsTransparencySupported` 方法。  
  
## <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocViewSDI#8](../mfc/codesnippet/cpp/cimage-limitations-with-earlier-operating-systems_1.cpp)]  
  
 若要編譯呼叫這些方法的應用程式，請在 #including 任何系統標頭前插入 #define _WIN32_WINNT 陳述式，表示 Windows 的版本等於或大於 5.0：  
  
 [!code-cpp[NVC_MFCDocViewSDI#9](../mfc/codesnippet/cpp/cimage-limitations-with-earlier-operating-systems_2.h)]  
  
 如果您的應用程式不需要在比 Windows 2000 或 Windows 98 舊的作業系統上執行，您可以直接與 msimg32.lib 連結而不使用**/delayload**。  
  
 [Cimage](../atl-mfc-shared/reference/cimage-class.md#draw)行為方式會與 Windows NT 4.0 或 Windows 95，Windows 2000 和 Windows 98 搭配使用時。  
  
 如果您將編譯您的應用程式使用 _WIN32_WINNT 組小於 0x0500，**繪製**運作，但它將不會處理自動執行 Windows 2000 和 Windows 98 和更新版本的系統上的透明度。  
  
 如果您應用程式設定為 0x0500 的 _WIN32_WINNT 或更多，編譯**繪製**會處理自動執行 Windows 2000 或 Windows 98 和更新版本的系統上的透明度。 它也能運作，但不具透明度支援，與 Windows NT 4.0 和 Windows 95。不過，您必須使用**/delayload**延遲 msimg32 載入。與上述針對 LIB`AlphaBlend`和`TransparentBlt`。  
  
## <a name="see-also"></a>請參閱  
 [CImage 類別](../atl-mfc-shared/reference/cimage-class.md)
