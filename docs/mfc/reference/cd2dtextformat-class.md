---
title: "CD2DTextFormat 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- afxrendertarget/CD2DTextFormat
- CD2DTextFormat
dev_langs:
- C++
helpviewer_keywords:
- CD2DTextFormat class
ms.assetid: db194cec-9dae-4644-ab84-7c43b7164117
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 5f7347dbbad8290bfdc800cbacaf21400583a392
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dtextformat-class"></a>CD2DTextFormat 類別
IDWriteTextFormat 包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CD2DTextFormat : public CD2DResource;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DTextFormat::CD2DTextFormat](#cd2dtextformat)|建構 CD2DTextFormat 物件。|  
|[CD2DTextFormat:: ~ CD2DTextFormat](#cd2dtextformat__~cd2dtextformat)|解構函式。 D2D 文字格式化物件終結時呼叫。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DTextFormat::Create](#create)|建立 CD2DTextFormat。 (覆寫[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create)。)|  
|[CD2DTextFormat::Destroy](#destroy)|終結 CD2DTextFormat 物件。 (覆寫[CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy)。)|  
|[CD2DTextFormat::Get](#get)|傳回 IDWriteTextFormat 介面|  
|[CD2DTextFormat::GetFontFamilyName](#getfontfamilyname)|取得字型家族名稱的複本。|  
|[CD2DTextFormat::GetLocaleName](#getlocalename)|取得地區設定名稱的複本。|  
|[CD2DTextFormat::IsValid](#isvalid)|檢查資源的有效性 (覆寫[CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid)。)|  
|[CD2DTextFormat::ReCreate](#recreate)|重新建立 CD2DTextFormat。 (覆寫[CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate)。)|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CD2DTextFormat::operator IDWriteTextFormat *](#operator_idwritetextformat_star)|傳回 IDWriteTextFormat 介面|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CD2DTextFormat::m_pTextFormat](#m_ptextformat)|IDWriteTextFormat 指標。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DTextFormat](../../mfc/reference/cd2dtextformat-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxrendertarget.h  
  
##  <a name="a-namedtorcd2dtextformata--cd2dtextformatcd2dtextformat"></a><a name="_dtorcd2dtextformat"></a>CD2DTextFormat:: ~ CD2DTextFormat  
 解構函式。 D2D 文字格式化物件終結時呼叫。  
  
```  
virtual ~CD2DTextFormat();
```  
  
##  <a name="a-namecd2dtextformata--cd2dtextformatcd2dtextformat"></a><a name="cd2dtextformat"></a>CD2DTextFormat::CD2DTextFormat  
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
 DIP （」 與裝置無關像素 」） 單位中的字型的邏輯大小。 DIPequals 1/96 英吋。  
  
 `fontWeight`  
 值，指出文字物件的字型粗細。  
  
 `fontStyle`  
 值，指出文字物件的字型樣式。  
  
 `fontStretch`  
 值，指出文字物件的字型縮放。  
  
 `strFontLocale`  
 CString 物件所在的地區設定名稱。  
  
 `pFontCollection`  
 字型集合物件的指標。 當這是 NULL 時，表示系統字型集合。  
  
 `bAutoDestroy`  
 指出由擁有者 (pParentTarget) 將會終結物件。  
  
##  <a name="a-namecreatea--cd2dtextformatcreate"></a><a name="create"></a>CD2DTextFormat::Create  
 建立 CD2DTextFormat。  
  
```  
virtual HRESULT Create(CRenderTarget* */);
```  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。  
  
##  <a name="a-namedestroya--cd2dtextformatdestroy"></a><a name="destroy"></a>CD2DTextFormat::Destroy  
 終結 CD2DTextFormat 物件。  
  
```  
virtual void Destroy();
```  
  
##  <a name="a-namegeta--cd2dtextformatget"></a><a name="get"></a>CD2DTextFormat::Get  
 傳回 IDWriteTextFormat 介面  
  
```  
IDWriteTextFormat* Get();
```  
  
### <a name="return-value"></a>傳回值  
 如果物件尚未初始化為 NULL 的 IDWriteTextFormat 介面的指標。  
  
##  <a name="a-namegetfontfamilynamea--cd2dtextformatgetfontfamilyname"></a><a name="getfontfamilyname"></a>CD2DTextFormat::GetFontFamilyName  
 取得字型家族名稱的複本。  
  
```  
CString GetFontFamilyName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 CString 物件，其中包含目前的字型家族名稱。  
  
##  <a name="a-namegetlocalenamea--cd2dtextformatgetlocalename"></a><a name="getlocalename"></a>CD2DTextFormat::GetLocaleName  
 取得地區設定名稱的複本。  
  
```  
CString GetLocaleName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 CString 物件，其中包含目前地區設定名稱。  
  
##  <a name="a-nameisvalida--cd2dtextformatisvalid"></a><a name="isvalid"></a>CD2DTextFormat::IsValid  
 檢查資源的有效性  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果資源無效，則為 TRUE否則為 FALSE。  
  
##  <a name="a-namemptextformata--cd2dtextformatmptextformat"></a><a name="m_ptextformat"></a>CD2DTextFormat::m_pTextFormat  
 IDWriteTextFormat 指標。  
  
```  
IDWriteTextFormat* m_pTextFormat;  
```  
  
##  <a name="a-nameoperatoridwritetextformatstara--cd2dtextformatoperator-idwritetextformat"></a><a name="operator_idwritetextformat_star"></a>CD2DTextFormat::operator IDWriteTextFormat *  
 傳回 IDWriteTextFormat 介面  
  
```  
operator IDWriteTextFormat*();
```   
  
### <a name="return-value"></a>傳回值  
 如果物件尚未初始化為 NULL 的 IDWriteTextFormat 介面的指標。  
  
##  <a name="a-namerecreatea--cd2dtextformatrecreate"></a><a name="recreate"></a>CD2DTextFormat::ReCreate  
 重新建立 CD2DTextFormat。  
  
```  
virtual HRESULT ReCreate(CRenderTarget* */);
```  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

