---
title: ATL_DRAWINFO 結構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::ATL_DRAWINFO
- ATL_DRAWINFO
- ATL.ATL_DRAWINFO
dev_langs:
- C++
helpviewer_keywords:
- ATL_DRAWINFO structure
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0e04f5efae261a151489309e876298b56ec696db
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="atldrawinfo-structure"></a>ATL_DRAWINFO 結構
包含用於轉譯為各種目標，例如印表機、 中繼檔或 ActiveX 控制項的資訊。  
  
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
  
## <a name="members"></a>成員  
 `cbSize`  
 結構，以位元組為單位的大小。  
  
 **dwDrawAspect**  
 指定目標的表示方式。 表示可以包含內容、 圖示、 縮圖或列印文件。 如需可能值的清單，請參閱[DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318)和[DVASPECT2](http://msdn.microsoft.com/library/windows/desktop/ms688644)。  
  
 **lindex**  
 想要進行繪製作業目標的部分。 中的值而異的解譯**dwDrawAspect**成員。  
  
 **ptd**  
 指標[DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613)啟用繪圖最佳化，根據指定的外觀的結構。 請注意，較新的物件和容器支援最佳化的繪圖介面的支援以及這個成員。 一律不支援最佳化的繪圖介面的舊物件和容器指定**NULL**這個成員。  
  
 **hicTargetDev**  
 所指向的目標裝置之資訊內容**ptd**物件可以從中擷取裝置度量資訊，並測試裝置的功能。 如果**ptd**是**NULL**，該物件應該忽略中的值**hicTargetDev**成員。  
  
 **hdcDraw**  
 在其上繪製的裝置內容。 針對無視窗的物件， **hdcDraw**成員處於`MM_TEXT`對應模式比對包含視窗的用戶端座標其邏輯座標。 此外，裝置內容應該在相同的狀態與通常依傳遞`WM_PAINT`訊息。  
  
 **prcBounds**  
 指標[RECTL](http://msdn.microsoft.com/library/windows/desktop/dd162907)結構，指定矩形上**hdcDraw**在應該繪製的物件。 這個成員會控制的定位和延伸的物件。 這個成員應該是**NULL**繪製無視窗的就地使用中的物件。 在每個其他情況下， **NULL**不合法的值，而且應該會導致`E_INVALIDARG`錯誤碼。 如果容器通過非**NULL**無視窗物件，物件的值應該轉譯成指定的裝置內容和矩形的要求的外觀。 容器可以要求從無視窗物件來呈現物件的第二個、 非作用中的檢視，或是要列印的物件。  
  
 **prcWBounds**  
 如果**hdcDraw**中繼檔裝置內容 (請參閱[GetDeviceCaps](http://msdn.microsoft.com/library/windows/desktop/dd144877) Windows SDK 中)，這是一個指向**RECTL**結構，指定的週框中基礎中繼檔。 矩形結構包含視窗範圍和視窗的原點。 這些值可用於繪製中繼檔。 所指定的矩形**prcBounds**這巢狀**prcWBounds**矩形; 它們是在相同的座標空間。  
  
 **bOptimize**  
 非零，如果控制項的繪圖是要最佳化，否則為 0。 當您完成時，如果繪圖進行最佳化，就會自動還原裝置內容的狀態呈現。  
  
 **bZoomed**  
 非零，如果目標有縮放因數，否則為 0。 縮放因數會儲存在**ZoomNum**。  
  
 **bRectInHimetric**  
 為非零，如果維度的**prcBounds**中**HIMETRIC**，否則為 0。  
  
 **ZoomNum**  
 寬度和此物件呈現到其中的矩形的高度。 縮放因數，沿著 x 軸 （其目前的範圍內物件的原始大小的比例） 的目標是值**ZoomNum.cx**除以值**ZoomDen.cx**。 沿著 y 軸的縮放因數會以類似的方式達成。  
  
 **ZoomDen**  
 實際寬度和高度的目標。  
  
## <a name="remarks"></a>備註  
 此結構的典型用法就是資訊的擷取期間的呈現目標物件。 例如，您可以擷取從值`ATL_DRAWINFO`內的多載，您[CComControlBase::OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced)。  
  
 此結構會儲存用來呈現物件的目標裝置之外觀的相關資訊。 提供的資訊可用於螢幕、 印表機，或甚至中繼檔繪製。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlctl.h  
  
## <a name="see-also"></a>另請參閱  
 [結構](../../atl/reference/atl-structures.md)   
 [Iviewobject:: Draw](http://msdn.microsoft.com/library/windows/desktop/ms688655)   
 [CComControlBase::OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)





