---
title: "ATL_DRAWINFO Structure | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::ATL_DRAWINFO"
  - "ATL_DRAWINFO"
  - "ATL.ATL_DRAWINFO"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL_DRAWINFO structure"
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# ATL_DRAWINFO Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

包含用於呈現用於資訊的各種不同的目標，例如印表機、中繼檔 \(Metafile\) 或 ActiveX 控制項。  
  
## 語法  
  
```  
  
      struct ATL_DRAWINFO{  
   UINT cbSize;  
   DWORD dwDrawAspect;  
   LONG lindex;  
   DVTARGETDEVICE* ptd;  
   HDC hicTargetDev;  
   HDC hdcDraw;  
   LPCRECTL prcBounds;  
   LPCRECTL prcWBounds;  
   BOOL bOptimize;  
   BOOL bZoomed;  
   BOOL bRectInHimetric;  
   SIZEL ZoomNum;  
   SIZEL ZoomDen;  
};  
```  
  
## Members  
 `cbSize`  
 結構的大小，以位元組為單位\)。  
  
 **dwDrawAspect**  
 指定目標如何表示。  表示可包含內容、圖示、縮圖、可列印的文件。  如需可能值的清單，請參閱 [DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318) 和 [DVASPE CT2](http://msdn.microsoft.com/library/windows/desktop/ms688644)。  
  
 **lindex**  
 進行繪製作業的整體目標的部分。  其說明根據 **dwDrawAspect** 成員值的變更。  
  
 **ptd**  
 根據指定的外觀啟用繪圖最佳化的 [DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613) 結構的指標。  請注意較新物件和容器支援最佳化的繪圖介面支援成員。  不支援最佳化的繪圖介面的舊物件和容器為成員一定會指定 **NULL** 。  
  
 **hicTargetDev**  
 目標裝置的資訊內容所指向的物件可以擷取裝置度量資訊 \(Metric\) 的 **ptd** 和測試裝置的功能。  如果是， **ptdNULL**物件應該忽略在 **hicTargetDev** 成員的值。  
  
 **hdcDraw**  
 裝置內容中繪製的。  對於無視窗的物件，是在 `MM_TEXT` 對應與其邏輯座標的 **hdcDraw** 成員模式比對包含視窗的工作區座標。  此外，裝置內容應在狀態和 `WM_PAINT` 訊息通常是透過的相同。  
  
 **prcBounds**  
 為 [RECTL](http://msdn.microsoft.com/library/windows/desktop/dd162907) 結構的指標指定的矩形。 **hdcDraw** 以及要繪製物件。  這個成員控制項位置和自動縮放物件。  這個成員應該是繪製無視窗就地啟動物件的 **NULL** 。  在其他情況下， **NULL** 不合法值，且應產生 `E_INVALIDARG` 錯誤碼。  如果容器將非**NULL** 值組無視窗的物件，該物件應該呈現需求方面讀入指定的裝置內容和矩形。  容器可以要求它從無視窗物件呈現物件的第二個，非現用檢視表或列印物件。  
  
 **prcWBounds**  
 如果 **hdcDraw** 是中繼檔 \(Metafile\) 裝置內容 \(請參閱在 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [GetDeviceCaps](http://msdn.microsoft.com/library/windows/desktop/dd144877) \)，這是 **RECTL** 結構指定的週框 \(Bounding Rectangle\) 的指標移至這個基礎中繼檔。  矩形結構包含 Windows 範圍和視窗原點。  這些值會繪製中繼檔會很有用。  **prcBounds** 運算式的矩形以巢狀方式位於這個 **prcWBounds** 矩形內，它們在同一個座標空間。  
  
 **bOptimize**  
 如果不是零，則控制項的繪製要最佳化，則為 0。  如果這個繪圖最佳化，裝置內容的狀態會自動還原，完成轉換時間。  
  
 **bZoomed**  
 不是零，如果目標具有縮放因數，則為 0。  縮放因數。 **ZoomNum**儲存。  
  
 **bRectInHimetric**  
 如果不是零，維度 **prcBounds** 在 **HIMETRIC**，則為 0。  
  
 **ZoomNum**  
 物件會呈現矩形的寬度和高度。  沿著 X 軸 \(物件的自然大小的比例來縮放因數在目前的範圍內\) 目標是 **ZoomNum.cx** 的值是由 **ZoomDen.cx**的值除以了。  沿著 Y 軸的縮放因數來達成。  
  
 **ZoomDen**  
 目標的實際寬度和高度。  
  
## 備註  
 目標物件的轉換時，這個結構的一般用法是擷取資訊。  例如，您可以從 \[ [CComControlBase::OnDrawAdvanced](../Topic/CComControlBase::OnDrawAdvanced.md)內的多載的 `ATL_DRAWINFO` 擷取值。  
  
 這個結構會儲存應用程式的相關資訊呈現物件的外觀目標裝置的。  所提供的資訊可在螢幕、印表機，甚至是中繼檔的繪圖。  
  
## 需求  
 **Header:** atlctl.h  
  
## 請參閱  
 [結構](../../atl/reference/atl-structures.md)   
 [IViewObject::Draw](http://msdn.microsoft.com/library/windows/desktop/ms688655)   
 [CComControlBase::OnDrawAdvanced](../Topic/CComControlBase::OnDrawAdvanced.md)