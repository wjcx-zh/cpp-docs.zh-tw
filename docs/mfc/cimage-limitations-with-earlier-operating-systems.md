---
title: "舊版作業系統上的 CImage 限制 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CImage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CImage 類別, 限制"
ms.assetid: 4bedaab8-7dd1-4c91-ab35-b75fb56765b0
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 舊版作業系統上的 CImage 限制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

許多 `CImage` 函式只與視窗一起使用新版本：Windows 95\/98 或 Windows NT 4.0、Windows 2000。  本文說明某些方法版本限制。  
  
 [CImage::PlgBlt](../Topic/CImage::PlgBlt.md) 和 [CImage::MaskBlt](../Topic/CImage::MaskBlt.md) 只有 Windows NT 4.0 \(含\) 以後版本搭配使用。  它們在以 Windows 95\/98 \(含\) 以後版本的應用程式無法運作。  
  
 因為您必須與 msimg32.lib 連接使用這些方法，[CImage::AlphaBlend](../Topic/CImage::AlphaBlend.md) 和 [CImage::TransparentBlt](../Topic/CImage::TransparentBlt.md) 與 Windows 2000 \(含\) 以後版本及只有 Windows 98 \(含\) 以後版本。\(這個程式庫對執行 Windows 2000 \(含\) 以後版本、Windows 98 \(含\) 以後版本的應用程式只能\)。  
  
 您可以在 Windows 95 或 Windows NT 4.0 上執行的應用程式可以包含 `AlphaBlend` 和 `TransparentBlt` ，只有這些方法絕對不會呼叫。  如果應用程式包含這些方法，因此，它在舊版作業系統上執行，您必須使用連結器的 [\/delayload](../build/reference/delayload-delay-load-import.md) msimg32.lib 延遲載入。  只要您的應用程式不會呼叫其中一個方法，在 Windows NT 4.0 或 Windows 95 上，它是不會嘗試載入 msimg32.lib。  您可以檢查支援透明度是否可以使用 `CImage::IsTransparencySupported` 方法。  
  
## 範例  
 [!code-cpp[NVC_MFCDocViewSDI#8](../mfc/codesnippet/CPP/cimage-limitations-with-earlier-operating-systems_1.cpp)]  
  
 若要編譯呼叫這些方法的應用程式，請在 \#including 任何系統標頭插入 \#define \_WIN32\_WINNT 陳述式，表示 Windows 版本等於或大於 5.0:  
  
 [!code-cpp[NVC_MFCDocViewSDI#9](../mfc/codesnippet/CPP/cimage-limitations-with-earlier-operating-systems_2.h)]  
  
 如果您的應用程式在作業系統舊比 Windows 2000 或 Windows 98 不需要執行，您可以直接與 msimg32.lib 連接，而不使用 **\/delayload**。  
  
 [CImage::Draw](../Topic/CImage::Draw.md) 會比對 Windows 4.0 或 Windows NT 95 有不同的行為，在使用 Windows 2000 和 Windows 98。  
  
 如果您編譯與 \_WIN32\_WINNT 的應用程式設定為小於 0x0500， **Draw** 中運作，不過，它在執行 Windows 2000 和 Windows 98 系統不會自動處理透明度 \(含\) 以後版本。  
  
 如果您編譯具有更大的 \_WIN32\_WINNT 的應用程式設定為 0x0500 **Draw** ，或在執行 Windows 2000 或 Windows 98 系統會自動處理透明度 \(含\) 以後版本。  它也會配合，，，但不含透明度支援，與 Windows NT 4.0、Windows 95;不過，您必須使用 **\/delayload** 延遲 msimg32.LIB 載入，將 `AlphaBlend` 和 `TransparentBlt`的。  
  
## 請參閱  
 [CImage Class](../atl-mfc-shared/reference/cimage-class.md)