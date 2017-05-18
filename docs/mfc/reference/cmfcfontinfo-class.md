---
title: "CMFCFontInfo 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::GetFullName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nCharSet
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nPitchAndFamily
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nType
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strScript
dev_langs:
- C++
helpviewer_keywords:
- CMFCFontInfo class
- CMFCFontInfo::CMFCFontInfo constructor
ms.assetid: f88329b2-d74e-4921-9441-a3bb6536a049
caps.latest.revision: 26
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: ac1409bcfce389cbc334edd2b864f7505d7443c7
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcfontinfo-class"></a>CMFCFontInfo 類別
`CMFCFontInfo`類別描述的名稱和字型的其他屬性。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCFontInfo : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|`CMFCFontInfo`|建構 `CMFCFontInfo` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCFontInfo::GetFullName](#getfullname)|擷取的字型和它的字元串連的名稱設定 （指令碼）。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCFontInfo::m_nCharSet](#m_ncharset)|值，指定與字型相關聯的字集 （指令碼）。|  
|[CMFCFontInfo::m_nPitchAndFamily](#m_npitchandfamily)|值，指定的頻率和字型系列。|  
|[CMFCFontInfo::m_nType](#m_ntype)|指定的字型類型的值。|  
|[CMFCFontInfo::m_strName](#m_strname)|字型; 的名稱例如，**新細明體**。|  
|[CMFCFontInfo::m_strScript](#m_strscript)|字元集 （指令碼） 相關聯之字型的名稱。|  
  
## <a name="remarks"></a>備註  
 您可以將附加`CMFCFontInfo`物件的項目[CMFCToolBarFontComboBox 類別](../../mfc/reference/cmfctoolbarfontcombobox-class.md)類別。 呼叫[CMFCToolBarFontComboBox::GetFontDesc](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc)方法來擷取變數的指標，`CMFCFontInfo`物件。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用的不同成員`CMFCFontInfo`類別。 範例將示範如何取得`CMFCFontInfo`物件從`CMFCRibbonFontComboBox`，以及如何存取其本機變數。 這個範例是屬於[MSOffice 2007 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo #&6;](../../mfc/reference/codesnippet/cpp/cmfcfontinfo-class_1.cpp)]  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxtoolbarfontcombobox.h  
  
##  <a name="cmfcfontinfo"></a>CMFCFontInfo::CMFCFontInfo  
 建構 `CMFCFontInfo` 物件。  
  
```  
CMFCFontInfo(
    LPCTSTR lpszName,  
    LPCTSTR lpszScript,  
    BYTE nCharSet,  
    BYTE nPitchAndFamily,  
    int nType);  
  
CMFCFontInfo(const CMFCFontInfo& src);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszName`  
 字型的名稱。 如需詳細資訊，請參閱`lfFaceName`成員[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)結構。  
  
 [in] `lpszScript`  
 指令碼 （字元集） 的字型名稱。  
  
 [in] `nCharSet`  
 指定字型的字集 （指令碼） 的值。 如需詳細資訊，請參閱`lfCharSet`成員[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)結構。  
  
 [in] `nPitchAndFamily`  
 值，指定的頻率和字型系列。 如需詳細資訊，請參閱`lfPitchAndFamily`成員[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)結構。  
  
 [in] `nType`  
 指定字型類型的值。 這個參數可以是 DEVICE_FONTTYPE、 RASTER_FONTTYPE，和 TRUETYPE_FONTTYPE 合 (OR)。  
  
 [in] `src`  
 將現有`CMFCFontInfo`其成員會用來建構這個物件`CMFCFontInfo`物件。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 這份文件使用的詞彙*字元集*和*指令碼*交替。 A*指令碼*，這也就是書寫系統，是字元和規則，在一或多種語言撰寫這些字元的集合。 字元的集合包含字母和使用該指令碼中的標點符號。 比方說，拉丁指令碼會用於英文的唸在美國，和其字母包括從 A 到 Z 的字元。`lfCharSet`成員[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)結構指定的字元集。 例如，值`ANSI_CHARSET`指定[!INCLUDE[vcpransi](../../atl-mfc-shared/reference/includes/vcpransi_md.md)]字元集，其中包括拉丁文字母。  
  
##  <a name="getfullname"></a>CMFCFontInfo::GetFullName  
 擷取的字型和它的字元串連的名稱設定 （指令碼）。  
  
```  
CString GetFullName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 字串，包含字型的名稱和指令碼。  
  
### <a name="remarks"></a>備註  
 使用這個方法來取得字型的完整名稱。 例如，如果字型名稱是`Arial`以及字型指令碼為`Cyrillic`，這個方法會傳回"新細明體 （斯拉夫） 」。  
  
##  <a name="m_ncharset"></a>CMFCFontInfo::m_nCharSet  
 值，指定與字型相關聯的字集 （指令碼）。  
  
```  
const BYTE m_nCharSet;  
```  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱`nCharSet`參數[CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo)建構函式。  
  
##  <a name="m_npitchandfamily"></a>CMFCFontInfo::m_nPitchAndFamily  
 指定的頻率 （點大小） 和字型家族 （例如，細明體，新細明體和等寬） 的值。  
  
```  
const BYTE m_nPitchAndFamily;  
```  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱`nPitchAndFamily`參數[CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo)建構函式。  
  
##  <a name="m_ntype"></a>CMFCFontInfo::m_nType  
 指定的字型類型的值。  
  
```  
const int m_nType;  
```  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱`nType`參數[CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo)建構函式。  
  
##  <a name="m_strname"></a>CMFCFontInfo::m_strName  
 字型的名稱︰ 例如，**新細明體**。  
  
```  
const CString m_strName;  
```  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱`lpszName`參數[CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo)建構函式。  
  
##  <a name="m_strscript"></a>CMFCFontInfo::m_strScript  
 字元集 （指令碼） 相關聯之字型的名稱。  
  
```  
const CString m_strScript;  
```  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱`lpszScript`參數[CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo)建構函式。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarFontComboBox 類別](../../mfc/reference/cmfctoolbarfontcombobox-class.md)   
 [CMFCToolBarFontSizeComboBox 類別](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)

