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
- CMFCMaskedEdit [MFC], DisableMask
- CMFCMaskedEdit [MFC], EnableGetMaskedCharsOnly
- CMFCMaskedEdit [MFC], EnableMask
- CMFCMaskedEdit [MFC], EnableSelectByGroup
- CMFCMaskedEdit [MFC], EnableSetMaskedCharsOnly
- CMFCMaskedEdit [MFC], GetWindowText
- CMFCMaskedEdit [MFC], SetValidChars
- CMFCMaskedEdit [MFC], SetWindowText
- CMFCMaskedEdit [MFC], IsMaskedChar
ms.assetid: 13b1a645-2d5d-4c37-8599-16d5003f23a5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b0ada987b3226d901c3bf01236c2a593c2e36f51
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcmaskededit-class"></a>CMFCMaskedEdit 類別
`CMFCMaskedEdit`類別支援遮罩的編輯控制項，會驗證使用者輸入，根據遮罩，並顯示根據範本驗證的結果。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCMaskedEdit : public CEdit  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|`CMFCMaskedEdit::CMFCMaskedEdit`|預設建構函式。|  
|`CMFCMaskedEdit::~CMFCMaskedEdit`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCMaskedEdit::DisableMask](#disablemask)|驗證使用者輸入停用。|  
|[CMFCMaskedEdit::EnableGetMaskedCharsOnly](#enablegetmaskedcharsonly)|指定是否`GetWindowText`方法會擷取不顯示字元的字元。|  
|[CMFCMaskedEdit::EnableMask](#enablemask)|初始化遮罩編輯控制項。|  
|[CMFCMaskedEdit::EnableSelectByGroup](#enableselectbygroup)|指定遮罩的編輯控制項是否會選取特定的使用者輸入或輸入的所有使用者的群組。|  
|[CMFCMaskedEdit::EnableSetMaskedCharsOnly](#enablesetmaskedcharsonly)|指定是否僅遮罩字元驗證文字，或針對整個遮罩。|  
|`CMFCMaskedEdit::GetThisClass`|由架構用來取得指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|  
|[CMFCMaskedEdit::GetWindowText](#getwindowtext)|擷取驗證遮罩的編輯控制項中的文字。|  
|[CMFCMaskedEdit::SetValidChars](#setvalidchars)|指定的使用者可以輸入的有效字元的字串。|  
|[CMFCMaskedEdit::SetWindowText](#setwindowtext)|遮罩的編輯控制項中顯示提示。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCMaskedEdit::IsMaskedChar](#ismaskedchar)|由架構呼叫以驗證指定的字元，針對對應的遮罩字元。|  
  
## <a name="remarks"></a>備註  
 執行下列步驟，以使用`CMFCMaskedEdit`應用程式中的控制項：  
  
 1. 內嵌`CMFCMaskedEdit`到您的視窗類別的物件。  
  
 2. 呼叫[CMFCMaskedEdit::EnableMask](#enablemask)方法，以指定的遮罩。  
  
 3. 呼叫[CMFCMaskedEdit::SetValidChars](#setvalidchars)方法，以指定有效的字元清單。  
  
 4. 呼叫[CMFCMaskedEdit::SetWindowText](#setwindowtext)方法，以指定的遮罩編輯控制項的預設文字。  
  
 5. 呼叫[CMFCMaskedEdit::GetWindowText](#getwindowtext)方法來擷取已驗證的文字。  
  
 如果您不會呼叫一或多個方法來初始化遮罩、 有效的字元和預設文字，遮罩的編輯控制項的行為就像標準的編輯控制項的行為。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用設定 （例如電話號碼） 的遮罩`EnableMask`方法來建立遮罩遮罩編輯控制項，`SetValidChars`方法，以指定的使用者可以輸入的有效字元和字串`SetWindowText`方法，以顯示在提示字元中遮罩編輯控制項。 這個範例是屬於[新控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#11](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#12](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCMaskedEdit](../../mfc/reference/cmfcmaskededit-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxmaskededit.h  
  
##  <a name="disablemask"></a>CMFCMaskedEdit::DisableMask  
 驗證使用者輸入停用。  
  
```  
void DisableMask();
```  
  
### <a name="remarks"></a>備註  
 如果已停用使用者輸入的驗證，遮罩的編輯控制項的行為方式與標準編輯控制項。  
  
##  <a name="enablegetmaskedcharsonly"></a>CMFCMaskedEdit::EnableGetMaskedCharsOnly  
 指定是否`GetWindowText`方法會擷取不顯示字元的字元。  
  
```  
void EnableGetMaskedCharsOnly(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bEnable`  
 `TRUE`若要指定[CMFCMaskedEdit::GetWindowText](#getwindowtext)方法擷取只遮罩字元。`FALSE`指定方法擷取整個文字。 預設值是 `TRUE`。  
  
### <a name="remarks"></a>備註  
 您可以使用這個方法來啟用擷取不顯示字元的字元。 然後建立對應至電話號碼，例如 (425) 555-0187 遮罩的編輯控制項。 如果您呼叫`GetWindowText`方法，它會傳回"4255550187"。 如果您停用擷取不顯示字元的字元，`GetWindowText`方法會傳回編輯控制項，例如"(425) 555-0187 」 中所顯示的文字。  
  
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
 [輸入] `lpszMask`  
 遮罩字串會指定可以出現在使用者輸入的每個位置的字元類型。 長度`lpszInputTemplate`和`lpszMask`參數字串必須相同。 請參閱 < 備註 > 一節，如需詳細資訊遮罩字元。  
  
 [輸入] `lpszInputTemplate`  
 遮罩範本字串，指定常值字元，可以出現在使用者輸入的每個位置。 使用底線字元 ('_') 做為字元預留位置。 長度`lpszInputTemplate`和`lpszMask`參數字串必須相同。  
  
 [輸入] `chMaskInputTemplate`  
 架構可以代替使用者輸入中每個無效字元的預設字元。 這個參數的預設值為底線 ('_')。  
  
 [輸入] `lpszValid`  
 字串，包含一組有效的字元。 `NULL`表示所有字元都都有效。 此參數的預設值為 `NULL`。  
  
### <a name="remarks"></a>備註  
 若要建立的遮罩遮罩的編輯控制項中使用這個方法。 自`CMFCMaskedEdit`類別並覆寫[CMFCMaskedEdit::IsMaskedChar](#ismaskedchar)方法，以自己的程式碼適用於自訂遮罩處理。  
  
 下表列出預設的遮罩字元：  
  
|遮罩字元|定義|  
|--------------------|----------------|  
|D|數字。|  
|d|數字或空格。|  
|+|加號 （'+ '）、 減號 ('-')，或空格。|  
|C|字母字元。|  
|c|字母字元或空格。|  
|A|英數字元。|  
|一個|英數字元或空格。|  
|*|可列印的字元。|  
  
##  <a name="enableselectbygroup"></a>CMFCMaskedEdit::EnableSelectByGroup  
 指定遮罩的編輯控制項是否允許使用者選取的特定群組的輸入或所有的輸入。  
  
```  
void EnableSelectByGroup(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bEnable`  
 `TRUE`若要選取群組。`FALSE`選取整個文字。 預設值是 `TRUE`。  
  
### <a name="remarks"></a>備註  
 您可以使用此函式來指定遮罩的編輯控制項是否允許使用者選取的群組或整個文字。  
  
 根據預設，會啟用選取的群組。 在此情況下使用者可以僅選取連續群組的有效字元。  
  
 例如，您可能會使用下列遮罩式的編輯控制驗證電話號碼：  
  
 `m_wndMaskEdit.EnableMask(`  
  
 `_T(" ddd  ddd dddd"),// Mask string`  
  
 `_T("(___) ___-____"),// Template string`  
  
 `_T(' '));// Default char`  
  
 `m_wndMaskEdit.SetValidChars(NULL); // All characters are valid.`  
  
 `m_wndMaskEdit.SetWindowText(_T("(425) 555-0187")); // Prompt`  
  
 如果選取項目依群組已啟用，使用者可以擷取只"425"、"555，"或"0187"字串群組。 如果群組選取項目已停用使用者可以擷取的電話號碼的全部文字: 「 (425) 555-0187"。  
  
##  <a name="enablesetmaskedcharsonly"></a>CMFCMaskedEdit::EnableSetMaskedCharsOnly  
 指定針對只不顯示字元的字元，或整個遮罩，是否驗證文字。  
  
```  
void EnableSetMaskedCharsOnly(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bEnable`  
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
  
 [輸入] `nMaxCount`  
 要接收的字元數目上限。  
  
 [輸出] `rstrString`  
 接收從編輯控制項的文字字串物件的參考。  
  
### <a name="return-value"></a>傳回值  
 第一個方法多載會傳回字串複製到的位元組數目`lpszStringBuf`參數緩衝區，則為 0，如果遮罩的編輯控制項不的任何文字。  
  
### <a name="remarks"></a>備註  
 這個方法會將文字複製到遮罩的編輯控制項中`lpszStringBuf`緩衝區或`rstrString`字串。  
  
 這個方法會重新定義[CWnd::GetWindowText](../../mfc/reference/cwnd-class.md#getwindowtext)。  
  
##  <a name="ismaskedchar"></a>CMFCMaskedEdit::IsMaskedChar  
 由架構呼叫以驗證指定的字元，針對對應的遮罩字元。  
  
```  
virtual BOOL IsMaskedChar(
    TCHAR chChar,  
    TCHAR chMaskChar) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸入] `chChar`  
 要驗證的字元。  
  
 [輸入] `chMaskChar`  
 遮罩字串中的對應字元。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果`chChar`參數是所允許的字元類型`chMaskChar`參數，否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 覆寫此方法以驗證您自己的輸入的字元。 如需遮罩字元的詳細資訊，請參閱[CMFCMaskedEdit::EnableMask](#enablemask)方法。  
  
##  <a name="setvalidchars"></a>CMFCMaskedEdit::SetValidChars  
 指定的使用者可以輸入的有效字元的字串。  
  
```  
void SetValidChars(LPCTSTR lpszValid=NULL);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszValid`  
 包含一組有效的輸入字元的字串。 `NULL`表示所有字元都都有效。 此參數的預設值為 `NULL`。  
  
### <a name="remarks"></a>備註  
 使用這個方法來定義有效的字元清單。 輸入的字元不在此清單中，如果遮罩的編輯控制項不會接受它。  
  
 下列程式碼範例只接受十六進位數字。  
  
 `//Mask: 0xFFFFm_wndMaskEdit.EnableMask( _T(" AAAA"),                // The mask string. _T("0x____"),               // The literal template string. _T('_'));                   // The default character that replaces the backspace character.// Valid string charactersm_wndMaskEdit.SetValidChars(_T("1234567890ABCDEFabcdef"));m_wndMaskEdit.SetWindowText(_T("0x01AF"));`  
  
##  <a name="setwindowtext"></a>CMFCMaskedEdit::SetWindowText  
 遮罩的編輯控制項中顯示提示。  
  
```  
void SetWindowText(LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszString`  
 指向以 null 結束的字串將用於做為提示。  
  
### <a name="remarks"></a>備註  
 這個方法會設定控制項的文字。  
  
 這個方法會重新定義[CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)。  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CEdit 類別](../../mfc/reference/cedit-class.md)
