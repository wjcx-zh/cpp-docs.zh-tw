---
title: "CMFCMaskedEdit 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCMaskedEdit
- AFXMASKEDEDIT/CMFCMaskedEdit
- AFXMASKEDEDIT/CMFCMaskedEdit::DisableMask
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableGetMaskedCharsOnly
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableMask
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableSelectByGroup
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableSetMaskedCharsOnly
- AFXMASKEDEDIT/CMFCMaskedEdit::GetWindowText
- AFXMASKEDEDIT/CMFCMaskedEdit::SetValidChars
- AFXMASKEDEDIT/CMFCMaskedEdit::SetWindowText
- AFXMASKEDEDIT/CMFCMaskedEdit::IsMaskedChar
dev_langs:
- C++
helpviewer_keywords:
- CMFCMaskedEdit class
- CMFCMaskedEdit constructor
ms.assetid: 13b1a645-2d5d-4c37-8599-16d5003f23a5
caps.latest.revision: 30
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
ms.openlocfilehash: 174551ecd75df8691d2a6086cbc074516f6d2045
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcmaskededit-class"></a>CMFCMaskedEdit 類別
`CMFCMaskedEdit`類別支援遮罩的編輯控制項，會根據遮罩驗證使用者輸入，並顯示根據範本驗證的結果。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCMaskedEdit : public CEdit  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|`CMFCMaskedEdit::CMFCMaskedEdit`|預設建構函式。|  
|`CMFCMaskedEdit::~CMFCMaskedEdit`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCMaskedEdit::DisableMask](#disablemask)|停用驗證使用者輸入。|  
|[CMFCMaskedEdit::EnableGetMaskedCharsOnly](#enablegetmaskedcharsonly)|指定是否`GetWindowText`方法會擷取僅遮罩的字元。|  
|[CMFCMaskedEdit::EnableMask](#enablemask)|初始化遮罩編輯控制項。|  
|[CMFCMaskedEdit::EnableSelectByGroup](#enableselectbygroup)|指定遮罩的編輯控制項是否會選取特定的使用者輸入或輸入的所有使用者的群組。|  
|[CMFCMaskedEdit::EnableSetMaskedCharsOnly](#enablesetmaskedcharsonly)|指定是否遮罩字元，僅針對驗證文字，或針對整個遮罩。|  
|`CMFCMaskedEdit::GetThisClass`|由架構用來取得變數的指標， [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與這個類別的型別相關聯的物件。|  
|[CMFCMaskedEdit::GetWindowText](#getwindowtext)|擷取驗證遮罩的編輯控制項中的文字。|  
|[CMFCMaskedEdit::SetValidChars](#setvalidchars)|指定的使用者可以輸入的有效字元的字串。|  
|[CMFCMaskedEdit::SetWindowText](#setwindowtext)|遮罩的編輯控制項中顯示提示。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCMaskedEdit::IsMaskedChar](#ismaskedchar)|驗證指定的字元對應遮罩字元對架構所呼叫。|  
  
## <a name="remarks"></a>備註  
 執行下列步驟，以使用`CMFCMaskedEdit`應用程式中的控制項︰  
  
 1. 內嵌`CMFCMaskedEdit`到您的視窗類別的物件。  
  
 2. 呼叫[CMFCMaskedEdit::EnableMask](#enablemask)方法，以指定的遮罩。  
  
 3. 呼叫[CMFCMaskedEdit::SetValidChars](#setvalidchars)方法，以指定的有效字元清單。  
  
 4. 呼叫[CMFCMaskedEdit::SetWindowText](#setwindowtext)方法，以指定的遮罩編輯控制項的預設文字。  
  
 5. 呼叫[CMFCMaskedEdit::GetWindowText](#getwindowtext)方法來擷取已驗證的文字。  
  
 如果您未呼叫一或多個方法來初始化遮罩、 有效的字元和預設文字，遮罩的編輯控制項的行為就像標準編輯控制項的行為。  
  
## <a name="example"></a>範例  
 下列範例示範如何設定 （例如電話號碼） 的遮罩使用`EnableMask`方法，以遮罩編輯控制項中，建立遮罩`SetValidChars`方法，以指定的使用者可以輸入，有效字元的字串和`SetWindowText`方法來顯示提示中遮罩編輯控制項。 這個範例是屬於[新的控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls #&11;](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls #&12;](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCMaskedEdit](../../mfc/reference/cmfcmaskededit-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxmaskededit.h  
  
##  <a name="disablemask"></a>CMFCMaskedEdit::DisableMask  
 停用驗證使用者輸入。  
  
```  
void DisableMask();
```  
  
### <a name="remarks"></a>備註  
 如果使用者輸入的驗證已停用，遮罩的編輯控制項的行為方式與標準編輯控制項。  
  
##  <a name="enablegetmaskedcharsonly"></a>CMFCMaskedEdit::EnableGetMaskedCharsOnly  
 指定是否`GetWindowText`方法會擷取僅遮罩的字元。  
  
```  
void EnableGetMaskedCharsOnly(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 `TRUE`若要指定[CMFCMaskedEdit::GetWindowText](#getwindowtext)方法擷取只遮罩字元。`FALSE`指定方法擷取整個文字。 預設值是 `TRUE`。  
  
### <a name="remarks"></a>備註  
 使用這個方法，以便擷取遮罩的字元。 然後建立相對應的電話號碼，例如 (425) 555-0187 遮罩的編輯控制項。 如果您呼叫`GetWindowText`方法，它會傳回 「&42555;50187 」。 如果您停用擷取遮罩的字元，`GetWindowText`方法會傳回顯示在編輯控制項，例如 「 (425) 555-0187 」 的文字。  
  
##  <a name="enablemask"></a>CMFCMaskedEdit::EnableMask  
 初始化遮罩編輯控制項。  
  
```  
void EnableMask(
    LPCTSTR lpszMask,  
    LPCTSTR lpszInputTemplate,  
    TCHAR chMaskInputTemplate=_T('_'),  
    LPCTSTR lpszValid=NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszMask`  
 遮罩的字串，指定可以出現在使用者輸入的每個位置的字元類型。 長度`lpszInputTemplate`和`lpszMask`參數字串必須相同。 請參閱 < 備註 > 一節，如需詳細資訊遮罩字元。  
  
 [in] `lpszInputTemplate`  
 遮罩範本字串，指定常值字元，可以出現在使用者輸入的每個位置。 使用底線字元 ('_') 做為字元預留位置。 長度`lpszInputTemplate`和`lpszMask`參數字串必須相同。  
  
 [in] `chMaskInputTemplate`  
 架構會為每個無效的字元，在使用者輸入替代的預設字元。 這個參數的預設值是底線 ('_')。  
  
 [in] `lpszValid`  
 字串，其中包含一組有效的字元。 `NULL`表示所有字元都都有效。 此參數的預設值為 `NULL`。  
  
### <a name="remarks"></a>備註  
 您可以使用這個方法來建立遮罩的編輯控制項的遮罩。 自`CMFCMaskedEdit`類別並覆寫[CMFCMaskedEdit::IsMaskedChar](#ismaskedchar)方法，以使用您自己的程式碼的自訂遮罩處理。  
  
 下表列出預設遮罩字元︰  
  
|遮罩字元|定義|  
|--------------------|----------------|  
|D|數字。|  
|d|數字或空格。|  
|+|加號 （'+ '）、 減號 ('-')，或空格。|  
|C|字母字元。|  
|c|字母字元或空格。|  
|A|英數字元。|  
|a|英數字元或空格。|  
|*|可列印的字元。|  
  
##  <a name="enableselectbygroup"></a>CMFCMaskedEdit::EnableSelectByGroup  
 指定是否遮罩的編輯控制項可讓使用者選取的特定群組的輸入或所有的輸入。  
  
```  
void EnableSelectByGroup(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 `TRUE`若要選取群組。`FALSE`選取整個文字。 預設值是 `TRUE`。  
  
### <a name="remarks"></a>備註  
 使用此函式指定遮罩的編輯控制項是否允許使用者選取的群組或整個文字。  
  
 根據預設，會啟用選取的群組。 在此情況下使用者可以選取只連續群組的有效字元。  
  
 例如，您可能使用下列遮罩的編輯控制項來驗證電話號碼︰  
  
 `m_wndMaskEdit.EnableMask(`  
  
 `_T(" ddd  ddd dddd"),// Mask string`  
  
 `_T("(___) ___-____"),// Template string`  
  
 `_T(' '));// Default char`  
  
 `m_wndMaskEdit.SetValidChars(NULL); // All characters are valid.`  
  
 `m_wndMaskEdit.SetWindowText(_T("(425) 555-0187")); // Prompt`  
  
 如果已啟用選取的群組，使用者可以擷取只"425"、"555 」 或 「&0187; 」 字串群組。 如果已停用群組選取項目，使用者可以擷取的電話號碼的全部文字: 「 (425) 555-0187 」。  
  
##  <a name="enablesetmaskedcharsonly"></a>CMFCMaskedEdit::EnableSetMaskedCharsOnly  
 指定是否針對只有遮罩字元，或整個遮罩會進行驗證的文字。  
  
```  
void EnableSetMaskedCharsOnly(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 `TRUE`若要驗證使用者輸入只遮罩字元;`FALSE`整個遮罩對其進行驗證。 預設值是 `TRUE`。  
  
##  <a name="getwindowtext"></a>CMFCMaskedEdit::GetWindowText  
 擷取驗證遮罩的編輯控制項中的文字。  
  
```  
int GetWindowText(
    LPTSTR lpszStringBuf,  
    int nMaxCount) const;  
  
void GetWindowText(CString& rstrString) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `lpszStringBuf`  
 接收從編輯控制項的文字緩衝區的指標。  
  
 [in] `nMaxCount`  
 要接收的字元數目上限。  
  
 [輸出] `rstrString`  
 接收從編輯控制項的文字字串物件的參考。  
  
### <a name="return-value"></a>傳回值  
 第一個方法多載會傳回字串，複製到的位元組數目`lpszStringBuf`參數緩衝區，則為 0，如果遮罩的編輯控制項中不有任何文字。  
  
### <a name="remarks"></a>備註  
 這個方法會將文字複製到遮罩的編輯控制項中`lpszStringBuf`緩衝區或`rstrString`字串。  
  
 這個方法來重新定義[CWnd::GetWindowText](../../mfc/reference/cwnd-class.md#getwindowtext)。  
  
##  <a name="ismaskedchar"></a>CMFCMaskedEdit::IsMaskedChar  
 驗證指定的字元對應遮罩字元對架構所呼叫。  
  
```  
virtual BOOL IsMaskedChar(
    TCHAR chChar,  
    TCHAR chMaskChar) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `chChar`  
 要驗證的字元。  
  
 [in] `chMaskChar`  
 遮罩字串中的對應字元。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果`chChar`參數是所允許的字元類型`chMaskChar`參數，否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，以驗證您自己的輸入的字元。 如需遮罩字元的詳細資訊，請參閱[CMFCMaskedEdit::EnableMask](#enablemask)方法。  
  
##  <a name="setvalidchars"></a>CMFCMaskedEdit::SetValidChars  
 指定的使用者可以輸入的有效字元的字串。  
  
```  
void SetValidChars(LPCTSTR lpszValid=NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszValid`  
 包含一組有效的輸入字元的字串。 `NULL`所有字元都是有效的方法。 此參數的預設值為 `NULL`。  
  
### <a name="remarks"></a>備註  
 使用這個方法來定義的有效字元清單。 如果輸入的字元不在此清單中，遮罩的編輯控制項不會接受它。  
  
 下列程式碼範例只接受十六進位數字。  
  
 `//Mask: 0xFFFFm_wndMaskEdit.EnableMask( _T(" AAAA"),                // The mask string. _T("0x____"),               // The literal template string. _T('_'));                   // The default character that replaces the backspace character.// Valid string charactersm_wndMaskEdit.SetValidChars(_T("1234567890ABCDEFabcdef"));m_wndMaskEdit.SetWindowText(_T("0x01AF"));`  
  
##  <a name="setwindowtext"></a>CMFCMaskedEdit::SetWindowText  
 遮罩的編輯控制項中顯示提示。  
  
```  
void SetWindowText(LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszString`  
 指向以 null 終止的字串，將使用做為提示。  
  
### <a name="remarks"></a>備註  
 這個方法會設定控制項的文字。  
  
 這個方法來重新定義[CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CEdit 類別](../../mfc/reference/cedit-class.md)

