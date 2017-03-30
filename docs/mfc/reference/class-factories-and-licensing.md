---
title: "Class Factory 和授權 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.classes
dev_langs:
- C++
helpviewer_keywords:
- class factories, and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
caps.latest.revision: 13
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
ms.sourcegitcommit: 3d045736f9a54d344c67e3f7408198e65a0bc95f
ms.openlocfilehash: 17a99edadeb7a5bd923126bce7fbef50313e1867
ms.lasthandoff: 03/29/2017

---
# <a name="class-factories-and-licensing"></a>Class Factory 和授權
若要建立 OLE 控制項的執行個體，容器應用程式會呼叫控制項之 Class Factory 的成員函式。 由於您的控制項是一個實際的 OLE 物件，Class Factory 會負責為您的控制項建立執行個體。 每個 OLE 控制項類別必須有一個 Class Factory。  
  
 OLE 控制項的另一個重要功能是其強制執行授權的能力。 ControlWizard 可讓您在專案建立控制項期間合併授權。 如需控制項授權的詳細資訊，請參閱文章[ActiveX 控制項︰ 授權 ActiveX 控制項](../../mfc/mfc-activex-controls-licensing-an-activex-control.md)。  
  
 下表列出用於幾個用於宣告和實作控制項的 Class Factory，以及控制項授權的巨集和函式。  
  
### <a name="class-factories-and-licensing"></a>Class Factory 和授權  
  
|||  
|-|-|  
|[DECLARE_OLECREATE_EX](#declare_olecreate_ex)|宣告 OLE 控制項或屬性頁面的 Class Factory。|  
|[IMPLEMENT_OLECREATE_EX](#implement_olecreate_ex)|實作控制項的 `GetClassID` 函式並宣告 Class Factory 的執行個體。|  
|[BEGIN_OLEFACTORY](#begin_olefactory)|所有授權函式宣告的開頭。|  
|[END_OLEFACTORY](#end_olefactory)|所有授權函式宣告的結尾。|  
|[AfxVerifyLicFile](#afxverifylicfile)|驗證控制項是否獲得在特定電腦上使用的授權。|  
  
##  <a name="declare_olecreate_ex"></a>DECLARE_OLECREATE_EX  
 宣告 class factory 和`GetClassID`控制類別成員函式。  
  
```   
DECLARE_OLECREATE_EX(class_name)   
```  
  
### <a name="parameters"></a>參數  
 *class_name*  
 控制項類別名稱。  
  
### <a name="remarks"></a>備註  
 使用這個巨集不支援授權控制項的控制項類別標頭檔中。  
  
 請注意，此巨集相同的目的為下列程式碼範例︰  
  
 [!code-cpp[NVC_MFCAxCtl # 14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]  
  
### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
  
##  <a name="implement_olecreate_ex"></a>IMPLEMENT_OLECREATE_EX  
 實作控制項的 class factory 和[GetClassID](../../mfc/reference/colecontrol-class.md#getclassid)控制類別成員函式。  
  
```   
IMPLEMENT_OLECREATE_EX(
   class_name,   
    external_name,    
    l,   
    w1,   
    w2,   
    b1,   
    b2,   
    b3,   
    b4,   
    b5,   
    b6,   
    b7,
    b8)   
```  
  
### <a name="parameters"></a>參數  
 *class_name*  
 控制項屬性頁類別名稱。  
  
 *external_name*  
 應用程式所公開物件名稱。  
  
 *l、 w1、 w2、 b1、 b2、 b3、 b4、 b5、 b6、 b7、 b8*  
 此類別的元件**CLSID**。 如需這些參數的詳細資訊，請參閱備註[IMPLEMENT_OLECREATE](run-time-object-model-services.md#implement_olecreate)。  
  
### <a name="remarks"></a>備註  
 這個巨集必須使用任何控制項類別的實作檔中出現`DECLARE_OLECREATE_EX`巨集或`BEGIN_OLEFACTORY`和`END_OLEFACTORY`巨集。 External name 是公開給其他應用程式的 OLE 控制項的識別碼。 容器會使用此名稱來要求此控制類別的物件。  
  
### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
  
##  <a name="begin_olefactory"></a>BEGIN_OLEFACTORY  
 開始您的類別處理站，您的控制項類別的標頭檔中宣告。  
  
``` 
BEGIN_OLEFACTORY(class_name)  
```  
  
### <a name="parameters"></a>參數  
 *class_name*  
 指定的控制項類別的類別處理站，這是名稱。  
  
### <a name="remarks"></a>備註  
 宣告授權函式的類別處理站應該開始之後立即`BEGIN_OLEFACTORY`。  
  
### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
  
##  <a name="end_olefactory"></a>END_OLEFACTORY  
 宣告的結尾控制項的 class factory。  
  
```  
END_OLEFACTORY(class_name)   
```  
  
### <a name="parameters"></a>參數  
 *class_name*  
 這是其類別處理站控制項類別的名稱。  
  
### <a name="requirements"></a>需求  
  **標頭**afxctl.h  
  
##  <a name="afxverifylicfile"></a>AfxVerifyLicFile  
 呼叫此函式，以確認授權檔案是由命名`pszLicFileName`適用於 OLE 控制項。  
  
```   
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,  
    LPCTSTR  pszLicFileName,  
    LPOLESTR  pszLicFileContents,  
    UINT cch = -1); 
```  
  
### <a name="parameters"></a>參數  
 `hInstance`  
 執行個體控制代碼與授權控制項相關聯的 dll。  
  
 `pszLicFileName`  
 指向以 null 結尾字元字串，包含授權檔名。  
  
 `pszLicFileContents`  
 必須符合授權檔案的開頭找到序列的位元組序列的點。  
  
 `cch`  
 中的字元數`pszLicFileContents`。  
  
### <a name="return-value"></a>傳回值  
 如果授權檔案存在，而且在中的字元序列的開頭為非零`pszLicFileContents`; 否則為 0。  
  
### <a name="remarks"></a>備註  
 如果`cch`為-1，這個函式使用︰  
  
 [!code-cpp[NVC_MFC_Utilities # 36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]  

### <a name="requirements"></a>需求  
  **標頭**afxctl.h  

## <a name="see-also"></a>另請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)

