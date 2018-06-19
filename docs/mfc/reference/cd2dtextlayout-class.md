---
title: CD2DTextLayout 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout::CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout::Create
- AFXRENDERTARGET/CD2DTextLayout::Destroy
- AFXRENDERTARGET/CD2DTextLayout::Get
- AFXRENDERTARGET/CD2DTextLayout::GetFontFamilyName
- AFXRENDERTARGET/CD2DTextLayout::GetLocaleName
- AFXRENDERTARGET/CD2DTextLayout::IsValid
- AFXRENDERTARGET/CD2DTextLayout::ReCreate
- AFXRENDERTARGET/CD2DTextLayout::SetFontFamilyName
- AFXRENDERTARGET/CD2DTextLayout::SetLocaleName
- AFXRENDERTARGET/CD2DTextLayout::m_pTextLayout
dev_langs:
- C++
helpviewer_keywords:
- CD2DTextLayout [MFC], CD2DTextLayout
- CD2DTextLayout [MFC], Create
- CD2DTextLayout [MFC], Destroy
- CD2DTextLayout [MFC], Get
- CD2DTextLayout [MFC], GetFontFamilyName
- CD2DTextLayout [MFC], GetLocaleName
- CD2DTextLayout [MFC], IsValid
- CD2DTextLayout [MFC], ReCreate
- CD2DTextLayout [MFC], SetFontFamilyName
- CD2DTextLayout [MFC], SetLocaleName
- CD2DTextLayout [MFC], m_pTextLayout
ms.assetid: 724bd13c-f2ef-4e55-a775-8cb04b7b7908
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 343d56ebf3f92dadeb286ae2fa44b6e735498215
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355921"
---
# <a name="cd2dtextlayout-class"></a>CD2DTextLayout 類別
IDWriteTextLayout 包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CD2DTextLayout : public CD2DResource;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DTextLayout::CD2DTextLayout](#cd2dtextlayout)|建構 CD2DTextLayout 物件。|  
|[CD2DTextLayout:: ~ CD2DTextLayout](#cd2dtextlayout__~cd2dtextlayout)|解構函式。 D2D 文字配置物件終結時呼叫。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DTextLayout::Create](#create)|建立 CD2DTextLayout。 (覆寫[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create)。)|  
|[CD2DTextLayout::Destroy](#destroy)|CD2DTextLayout 物件已遭終結。 (覆寫[CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy)。)|  
|[CD2DTextLayout::Get](#get)|傳回 IDWriteTextLayout 介面|  
|[CD2DTextLayout::GetFontFamilyName](#getfontfamilyname)|將複製的指定位置處的文字字型家族名稱。|  
|[CD2DTextLayout::GetLocaleName](#getlocalename)|取得位於指定位置的地區設定名稱的文字。|  
|[CD2DTextLayout::IsValid](#isvalid)|檢查資源的有效性 (會覆寫[CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid)。)|  
|[CD2DTextLayout::ReCreate](#recreate)|CD2DTextLayout 會重新建立。 (覆寫[CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate)。)|  
|[CD2DTextLayout::SetFontFamilyName](#setfontfamilyname)|設定以 null 結束的字型家族名稱中指定的文字範圍的文字|  
|[CD2DTextLayout::SetLocaleName](#setlocalename)|設定指定的文字範圍內文字的地區設定名稱|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DTextLayout::operator IDWriteTextLayout *](#operator_idwritetextlayout_star)|傳回 IDWriteTextLayout 介面|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DTextLayout::m_pTextLayout](#m_ptextlayout)|IDWriteTextLayout 指標。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DTextLayout](../../mfc/reference/cd2dtextlayout-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxrendertarget.h  
  
##  <a name="_dtorcd2dtextlayout"></a>  CD2DTextLayout:: ~ CD2DTextLayout  
 解構函式。 D2D 文字配置物件終結時呼叫。  
  
```  
virtual ~CD2DTextLayout();
```  
  
##  <a name="cd2dtextlayout"></a>  CD2DTextLayout::CD2DTextLayout  
 建構 CD2DTextLayout 物件。  
  
```  
CD2DTextLayout(
    CRenderTarget* pParentTarget,  
    const CString& strText,  
    CD2DTextFormat& textFormat,  
    const CD2DSizeF& sizeMax,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `pParentTarget`  
 呈現目標指標。  
  
 `strText`  
 CString 物件，其中包含要建立新 CD2DTextLayout 物件的字串。  
  
 `textFormat`  
 CString 物件，其中包含要套用至字串的格式。  
  
 `sizeMax`  
 [配置] 方塊的大小。  
  
 `bAutoDestroy`  
 表示擁有者 (pParentTarget) 將會終結物件。  
  
##  <a name="create"></a>  CD2DTextLayout::Create  
 建立 CD2DTextLayout。  
  
```  
virtual HRESULT Create(CRenderTarget* */);
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。  
  
##  <a name="destroy"></a>  CD2DTextLayout::Destroy  
 CD2DTextLayout 物件已遭終結。  
  
```  
virtual void Destroy();
```  
  
##  <a name="get"></a>  CD2DTextLayout::Get  
 傳回 IDWriteTextLayout 介面  
  
```  
IDWriteTextLayout* Get();
```  
  
### <a name="return-value"></a>傳回值  
 IDWriteTextLayout 介面或如果尚未初始化物件為 NULL 指標。  
  
##  <a name="getfontfamilyname"></a>  CD2DTextLayout::GetFontFamilyName  
 將複製的指定位置處的文字字型家族名稱。  
  
```  
CString GetFontFamilyName(
    UINT32 currentPosition,  
    DWRITE_TEXT_RANGE* textRange = NULL) const;  
```  
  
### <a name="parameters"></a>參數  
 `currentPosition`  
 檢查文字的位置。  
  
 `textRange`  
 具有相同的文字範圍的格式 currentPosition 所指定的位置處的文字。 這表示執行可讓您有確切的格式為指定的位置，包括但不是限於字型家族名稱。  
  
### <a name="return-value"></a>傳回值  
 CString 物件，其中包含目前的字型家族名稱。  
  
##  <a name="getlocalename"></a>  CD2DTextLayout::GetLocaleName  
 取得位於指定位置的地區設定名稱的文字。  
  
```  
CString GetLocaleName(
    UINT32 currentPosition,  
    DWRITE_TEXT_RANGE* textRange = NULL) const;  
```  
  
### <a name="parameters"></a>參數  
 `currentPosition`  
 檢查文字的位置。  
  
 `textRange`  
 具有相同的文字範圍的格式 currentPosition 所指定的位置處的文字。 這表示執行可讓您有確切的格式為指定的位置，包括但不是限於地區設定名稱。  
  
### <a name="return-value"></a>傳回值  
 CString 物件，其中包含目前地區設定名稱。  
  
##  <a name="isvalid"></a>  CD2DTextLayout::IsValid  
 檢查資源的有效性  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果資源有效，則為 TRUE否則為 FALSE。  
  
##  <a name="m_ptextlayout"></a>  CD2DTextLayout::m_pTextLayout  
 IDWriteTextLayout 指標。  
  
```  
IDWriteTextLayout* m_pTextLayout;  
```  
  
##  <a name="operator_idwritetextlayout_star"></a>  CD2DTextLayout::operator IDWriteTextLayout *  
 傳回 IDWriteTextLayout 介面  
  
```  
operator IDWriteTextLayout*();
```   
  
### <a name="return-value"></a>傳回值  
 IDWriteTextLayout 介面或如果尚未初始化物件為 NULL 指標。  
  
##  <a name="recreate"></a>  CD2DTextLayout::ReCreate  
 CD2DTextLayout 會重新建立。  
  
```  
virtual HRESULT ReCreate(CRenderTarget* */);
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。  
  
##  <a name="setfontfamilyname"></a>  CD2DTextLayout::SetFontFamilyName  
 設定以 null 結束的字型家族名稱中指定的文字範圍的文字  
  
```  
BOOL SetFontFamilyName(
    LPCWSTR pwzFontFamilyName,  
    DWRITE_TEXT_RANGE textRange);
```  
  
### <a name="parameters"></a>參數  
 `pwzFontFamilyName`  
 TextRange 所指定的範圍內的整個文字字串，適用於字型家族名稱  
  
 `textRange`  
 這項變更適用於文字範圍  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE  
  
##  <a name="setlocalename"></a>  CD2DTextLayout::SetLocaleName  
 設定指定的文字範圍內文字的地區設定名稱  
  
```  
BOOL SetLocaleName(
    LPCWSTR pwzLocaleName,  
    DWRITE_TEXT_RANGE textRange);
```  
  
### <a name="parameters"></a>參數  
 `pwzLocaleName`  
 以 null 結束的地區設定名稱字串  
  
 `textRange`  
 這項變更適用於文字範圍  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
