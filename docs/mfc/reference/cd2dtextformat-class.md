---
title: CD2DTextFormat 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat::CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat::Create
- AFXRENDERTARGET/CD2DTextFormat::Destroy
- AFXRENDERTARGET/CD2DTextFormat::Get
- AFXRENDERTARGET/CD2DTextFormat::GetFontFamilyName
- AFXRENDERTARGET/CD2DTextFormat::GetLocaleName
- AFXRENDERTARGET/CD2DTextFormat::IsValid
- AFXRENDERTARGET/CD2DTextFormat::ReCreate
- AFXRENDERTARGET/CD2DTextFormat::m_pTextFormat
dev_langs:
- C++
helpviewer_keywords:
- CD2DTextFormat [MFC], CD2DTextFormat
- CD2DTextFormat [MFC], Create
- CD2DTextFormat [MFC], Destroy
- CD2DTextFormat [MFC], Get
- CD2DTextFormat [MFC], GetFontFamilyName
- CD2DTextFormat [MFC], GetLocaleName
- CD2DTextFormat [MFC], IsValid
- CD2DTextFormat [MFC], ReCreate
- CD2DTextFormat [MFC], m_pTextFormat
ms.assetid: db194cec-9dae-4644-ab84-7c43b7164117
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e55689fa71ed5f0e4ebd4978a004212d5fb82b5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352886"
---
# <a name="cd2dtextformat-class"></a>CD2DTextFormat 類別
IDWriteTextFormat 包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CD2DTextFormat : public CD2DResource;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DTextFormat::CD2DTextFormat](#cd2dtextformat)|建構 CD2DTextFormat 物件。|  
|[CD2DTextFormat:: ~ CD2DTextFormat](#cd2dtextformat__~cd2dtextformat)|解構函式。 D2D 文字格式化物件終結時呼叫。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DTextFormat::Create](#create)|建立 CD2DTextFormat。 (覆寫[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create)。)|  
|[CD2DTextFormat::Destroy](#destroy)|CD2DTextFormat 物件已遭終結。 (覆寫[CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy)。)|  
|[CD2DTextFormat::Get](#get)|傳回 IDWriteTextFormat 介面|  
|[CD2DTextFormat::GetFontFamilyName](#getfontfamilyname)|取得一份字型家族名稱。|  
|[CD2DTextFormat::GetLocaleName](#getlocalename)|取得地區設定名稱的複本。|  
|[CD2DTextFormat::IsValid](#isvalid)|檢查資源的有效性 (會覆寫[CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid)。)|  
|[CD2DTextFormat::ReCreate](#recreate)|CD2DTextFormat 會重新建立。 (覆寫[CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate)。)|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DTextFormat::operator IDWriteTextFormat *](#operator_idwritetextformat_star)|傳回 IDWriteTextFormat 介面|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DTextFormat::m_pTextFormat](#m_ptextformat)|IDWriteTextFormat 指標。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DTextFormat](../../mfc/reference/cd2dtextformat-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxrendertarget.h  
  
##  <a name="_dtorcd2dtextformat"></a>  CD2DTextFormat:: ~ CD2DTextFormat  
 解構函式。 D2D 文字格式化物件終結時呼叫。  
  
```  
virtual ~CD2DTextFormat();
```  
  
##  <a name="cd2dtextformat"></a>  CD2DTextFormat::CD2DTextFormat  
 建構 CD2DTextFormat 物件。  
  
```  
CD2DTextFormat(
    CRenderTarget* pParentTarget,  
    const CString& strFontFamilyName,  
    FLOAT fontSize,  
    DWRITE_FONT_WEIGHT fontWeight = DWRITE_FONT_WEIGHT_NORMAL,  
    DWRITE_FONT_STYLE fontStyle = DWRITE_FONT_STYLE_NORMAL,  
    DWRITE_FONT_STRETCH fontStretch = DWRITE_FONT_STRETCH_NORMAL,  
    const CString& strFontLocale = _T(""),  
    IDWriteFontCollection* pFontCollection = NULL,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `pParentTarget`  
 呈現目標指標。  
  
 `strFontFamilyName`  
 CString 物件，其中包含字型家族的名稱。  
  
 `fontSize`  
 以 DIP （「 裝置獨立畫素"） 為單位之字型的邏輯大小。 DIPequals 1/96 英吋。  
  
 `fontWeight`  
 值，指出 「 文字 」 物件的字型粗細。  
  
 `fontStyle`  
 值，指出 「 文字 」 物件的字型樣式。  
  
 `fontStretch`  
 值，指出 「 文字 」 物件的字型縮放。  
  
 `strFontLocale`  
 CString 物件，其中包含地區設定名稱。  
  
 `pFontCollection`  
 字型集合物件的指標。 當這是 NULL 時，表示系統字型集合。  
  
 `bAutoDestroy`  
 表示擁有者 (pParentTarget) 將會終結物件。  
  
##  <a name="create"></a>  CD2DTextFormat::Create  
 建立 CD2DTextFormat。  
  
```  
virtual HRESULT Create(CRenderTarget* */);
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。  
  
##  <a name="destroy"></a>  CD2DTextFormat::Destroy  
 CD2DTextFormat 物件已遭終結。  
  
```  
virtual void Destroy();
```  
  
##  <a name="get"></a>  CD2DTextFormat::Get  
 傳回 IDWriteTextFormat 介面  
  
```  
IDWriteTextFormat* Get();
```  
  
### <a name="return-value"></a>傳回值  
 IDWriteTextFormat 介面或如果尚未初始化物件為 NULL 指標。  
  
##  <a name="getfontfamilyname"></a>  CD2DTextFormat::GetFontFamilyName  
 取得一份字型家族名稱。  
  
```  
CString GetFontFamilyName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 CString 物件，其中包含目前的字型家族名稱。  
  
##  <a name="getlocalename"></a>  CD2DTextFormat::GetLocaleName  
 取得地區設定名稱的複本。  
  
```  
CString GetLocaleName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 CString 物件，其中包含目前地區設定名稱。  
  
##  <a name="isvalid"></a>  CD2DTextFormat::IsValid  
 檢查資源的有效性  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果資源有效，則為 TRUE否則為 FALSE。  
  
##  <a name="m_ptextformat"></a>  CD2DTextFormat::m_pTextFormat  
 IDWriteTextFormat 指標。  
  
```  
IDWriteTextFormat* m_pTextFormat;  
```  
  
##  <a name="operator_idwritetextformat_star"></a>  CD2DTextFormat::operator IDWriteTextFormat *  
 傳回 IDWriteTextFormat 介面  
  
```  
operator IDWriteTextFormat*();
```   
  
### <a name="return-value"></a>傳回值  
 IDWriteTextFormat 介面或如果尚未初始化物件為 NULL 指標。  
  
##  <a name="recreate"></a>  CD2DTextFormat::ReCreate  
 CD2DTextFormat 會重新建立。  
  
```  
virtual HRESULT ReCreate(CRenderTarget* */);
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
