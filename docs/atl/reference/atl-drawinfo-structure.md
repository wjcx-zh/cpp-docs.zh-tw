---
title: "ATL_DRAWINFO 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::ATL_DRAWINFO
- ATL_DRAWINFO
- ATL.ATL_DRAWINFO
dev_langs:
- C++
helpviewer_keywords:
- ATL_DRAWINFO structure
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: bc124de97acf85d6e706605afb55b0747a327ade
ms.lasthandoff: 02/24/2017

---
# <a name="atldrawinfo-structure"></a>ATL_DRAWINFO 結構
包含用於不同的目標，例如印表機、 中繼檔或 ActiveX 控制項的呈現的資訊。  
  
## <a name="syntax"></a>語法  
  
```
struct ATL_DRAWINFO {
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
  
## <a name="members"></a>Members  
 `cbSize`  
 結構，以位元組為單位的大小。  
  
 **dwDrawAspect**  
 指定要呈現目標的方式。 表示可以包含內容、 圖示、 縮圖或列印的文件。 如需可能的值，請參閱[DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318)和[DVASPECT2](http://msdn.microsoft.com/library/windows/desktop/ms688644)。  
  
 **lindex**  
 部分是想要進行繪製作業的目標。 它的解譯方式中的值而異**dwDrawAspect**成員。  
  
 **ptd**  
 指標[DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613)啟用繪圖最佳化，根據指定的外觀的結構。 請注意，較新的物件和容器支援最佳化的繪圖介面的支援以及這個成員。 不一定支援最佳化的繪圖介面的較舊的物件和容器指定**NULL**這個成員。  
  
 **hicTargetDev**  
 所指向的目標裝置之資訊內容**ptd**物件可以從中擷取裝置度量資訊，並測試裝置的功能。 如果**ptd**是**NULL**，該物件應該忽略中的值**hicTargetDev**成員。  
  
 **hdcDraw**  
 在其上繪製的裝置內容。 無視窗物件時， **hdcDraw**成員處於`MM_TEXT`對應模式比對包含視窗的工作區座標的邏輯座標。 此外，裝置的內容應該在相同的狀態是一般傳遞`WM_PAINT`訊息。  
  
 **prcBounds**  
 指標[RECTL](http://msdn.microsoft.com/library/windows/desktop/dd162907)結構上指定的矩形**hdcDraw** ，在應該繪製物件。 這個成員控制項的定位和自動縮放的物件。 這個成員應該**NULL**繪製無視窗就地使用中的物件。 在每個其他情況下， **NULL**不合法的值，而且應該會導致`E_INVALIDARG`錯誤碼。 如果容器通過非**NULL**無視窗物件，該物件的值應該轉譯成指定之的裝置內容和矩形的要求的外觀。 容器可以向要求此資訊來呈現物件的第二個、 非作用中檢視或列印物件的無視窗物件。  
  
 **prcWBounds**  
 如果**hdcDraw**中繼檔裝置內容 (請參閱[GetDeviceCaps](http://msdn.microsoft.com/library/windows/desktop/dd144877)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)])，這是一個指向**RECTL**結構在基礎中繼檔中指定的周框矩形。 矩形結構包含視窗範圍和視窗原點。 這些值可用於繪製中繼檔。 以矩形表示**prcBounds**巢狀這**prcWBounds**矩形; 它們位於相同的座標空間。  
  
 **bOptimize**  
 如果控制項的繪圖是經過最佳化，否則為 0 為非零。 當您完成時，如果繪圖進行最佳化，會自動還原裝置內容的狀態呈現。  
  
 **bZoomed**  
 非零，如果目標的縮放因數，否則為 0。 縮放因數會儲存在**ZoomNum**。  
  
 **bRectInHimetric**  
 如果為非零的維度**prcBounds**位於**HIMETRIC**，否則為 0。  
  
 **ZoomNum**  
 寬度和此物件呈現到其中的矩形的高度。 縮放因數，沿著 x 軸 （其目前的範圍內物件的原始大小的比例） 的目標就是值**ZoomNum.cx**除以值**ZoomDen.cx**。 沿著 y 軸的縮放因數是以類似的方式來達成。  
  
 **ZoomDen**  
 實際寬度和高度的目標。  
  
## <a name="remarks"></a>備註  
 此結構的典型用法是資訊的擷取期間的呈現目標物件。 例如，您可以擷取的值`ATL_DRAWINFO`內您多載[CComControlBase::OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced)。  
  
 此結構會儲存用來呈現物件的目標裝置之外觀的相關資訊。 所提供的資訊可用於繪製到螢幕、 印表機或甚至中繼檔。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlctl.h  
  
## <a name="see-also"></a>另請參閱  
 [結構](../../atl/reference/atl-structures.md)   
 [Iviewobject:: Draw](http://msdn.microsoft.com/library/windows/desktop/ms688655)   
 [CComControlBase::OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)






