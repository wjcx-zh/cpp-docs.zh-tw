---
title: "圖形診斷擷取方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea21995d-0241-412e-8f62-600c3794247f
caps.latest.revision: 2
caps.handback.revision: 2
ms.author: "mithom"
manager: "douge"
---
# 圖形診斷擷取方法
在此插入簡介。  
  
## 擷取方法  
 在 [!INCLUDE[win81](../misc/includes/win81_md.md)] 中，DirectX 11.2 執行階段可以代表偵錯工具 \(如圖形診斷\) 在內部擷取圖形資訊；這稱為*「穩固擷取」*\(robust capture\)。  在此支援加入至 DirectX 執行階段之前，圖形資訊的擷取方式是先攔截特定 DirectX 函式呼叫來記錄引數和其他資訊，再將呼叫轉送給 DirectX 以完成；這稱為*「舊版擷取」*\(legacy capture\)。  
  
 因為只有 DirectX 執行階段才能在 [!INCLUDE[win81](../misc/includes/win81_md.md)] 中擷取圖形資訊，所以不需要更新舊版擷取來支援 DirectX 11.2，因此，舊版擷取已被取代。  不過，因為 DirectX 11.2 執行階段不支援 [!INCLUDE[win81](../misc/includes/win81_md.md)] 之前的 Windows 版本，所以針對將目標設為 [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)] 和 [!INCLUDE[win8](../build/includes/win8_md.md)] 的應用程式，[!INCLUDE[win7](../build/includes/win7_md.md)] 仍然支援舊版擷取。  
  
 這兩種方法都記錄類似的資訊，而且不會變更您擷取圖形資訊的方式，或使用圖形診斷工具的方式。  
  
### 穩固擷取  
 穩固擷取支援 [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)]、[!INCLUDE[win81](../misc/includes/win81_md.md)] 和 Windows Phone 8.1 上的 [!INCLUDE[winblue_winrt_2](../misc/includes/winblue_winrt_2_md.md)] 圖形診斷。  它支援 DirectX 10.0 到 DirectX 11.2，而且可以擷取新的 Direct3D 11.2 功能 \(例如，並排的資源\) 的圖形資訊。  不過，它未完全支援所有 Direct3D 11.2 功能 \(例如，您無法偵錯使用 HLSL 著色器連結功能所建立的 HLSL 著色器\)。  穩固擷取使用新的擷取 API，以支援其程式設計擷取情況。  
  
### 舊版擷取  
 舊版擷取支援 [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)]、Windows RT 8 和 [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] 上的 [!INCLUDE[win8](../build/includes/win8_md.md)] 和 [!INCLUDE[win7](../build/includes/win7_md.md)] 圖形診斷。  它支援 DirectX 10.0 到 DirectX 11.1。  舊版擷取不支援任何 Direct3D 11.2 功能且已被取代，但無法使用穩固擷取的情況除外。  舊版擷取使用 `vsgcapture.h` 標頭檔中所定義的擷取 API，以支援其程式設計擷取情況。  這類型的程式設計擷取也已被取代，但無法使用穩固擷取的情況除外。  
  
## 請參閱  
 [擷取圖形資訊](../Topic/Capturing%20Graphics%20Information.md)   
 [逐步解說：擷取圖形資訊](../Topic/Walkthrough:%20Capturing%20Graphics%20Information.md)