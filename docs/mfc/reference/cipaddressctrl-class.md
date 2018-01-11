---
title: "CIPAddressCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CIPAddressCtrl
- AFXCMN/CIPAddressCtrl
- AFXCMN/CIPAddressCtrl::CIPAddressCtrl
- AFXCMN/CIPAddressCtrl::ClearAddress
- AFXCMN/CIPAddressCtrl::Create
- AFXCMN/CIPAddressCtrl::CreateEx
- AFXCMN/CIPAddressCtrl::GetAddress
- AFXCMN/CIPAddressCtrl::IsBlank
- AFXCMN/CIPAddressCtrl::SetAddress
- AFXCMN/CIPAddressCtrl::SetFieldFocus
- AFXCMN/CIPAddressCtrl::SetFieldRange
dev_langs: C++
helpviewer_keywords:
- CIPAddressCtrl [MFC], CIPAddressCtrl
- CIPAddressCtrl [MFC], ClearAddress
- CIPAddressCtrl [MFC], Create
- CIPAddressCtrl [MFC], CreateEx
- CIPAddressCtrl [MFC], GetAddress
- CIPAddressCtrl [MFC], IsBlank
- CIPAddressCtrl [MFC], SetAddress
- CIPAddressCtrl [MFC], SetFieldFocus
- CIPAddressCtrl [MFC], SetFieldRange
ms.assetid: 9764d2f4-cb14-4ba8-b799-7f57a55a47c6
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 67c775f314cc70da1b662ca9b9c5f0a2e68eb2bc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cipaddressctrl-class"></a>CIPAddressCtrl 類別
提供 Windows 通用 IP 位址控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CIPAddressCtrl : public CWnd  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CIPAddressCtrl::CIPAddressCtrl](#cipaddressctrl)|建構 `CIPAddressCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CIPAddressCtrl::ClearAddress](#clearaddress)|清除 IP 位址控制項的內容。|  
|[CIPAddressCtrl::Create](#create)|建立 IP 位址控制項，並將它附加至`CIPAddressCtrl`物件。|  
|[CIPAddressCtrl::CreateEx](#createex)|使用指定的 Windows 延伸樣式建立 IP 位址控制項，並將它附加至`CIPAddressCtrl`物件。|  
|[CIPAddressCtrl::GetAddress](#getaddress)|擷取 IP 位址控制項中的所有四個欄位的位址值。|  
|[CIPAddressCtrl::IsBlank](#isblank)|決定是否 IP 位址控制項中的所有欄位都會空白。|  
|[CIPAddressCtrl::SetAddress](#setaddress)|設定 IP 位址控制項中的所有四個欄位的位址值。|  
|[CIPAddressCtrl::SetFieldFocus](#setfieldfocus)|將鍵盤焦點設定到 IP 位址控制項中的指定欄位。|  
|[CIPAddressCtrl::SetFieldRange](#setfieldrange)|IP 位址控制項中指定之欄位中設定的範圍。|  
  
## <a name="remarks"></a>備註  
 IP 位址控制項，類似於編輯控制項，控制項可讓您輸入及操作的網際網路通訊協定 (IP) 格式的數值位址。  
  
 這個控制項 (因此`CIPAddressCtrl`類別) 僅適用於在 Microsoft Internet Explorer 4.0 和更新版本中執行的程式。 它們也會出現在未來版本的 Windows 和 Windows NT 下。  
  
 多個一般 IP 位址控制項的詳細資訊，請參閱[IP 位址控制項](http://msdn.microsoft.com/library/windows/desktop/bb761372)Windows SDK 中。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CIPAddressCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
##  <a name="cipaddressctrl"></a>CIPAddressCtrl::CIPAddressCtrl  
 建立 `CIPAddressCtrl` 物件。  
  
```  
CIPAddressCtrl();
```  
  
##  <a name="clearaddress"></a>CIPAddressCtrl::ClearAddress  
 清除 IP 位址控制項的內容。  
  
```  
void ClearAddress();
```  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息行為[IPM_CLEARADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761377)、 Windows SDK 中所述。  
  
##  <a name="create"></a>CIPAddressCtrl::Create  
 建立 IP 位址控制項，並將它附加至`CIPAddressCtrl`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 IP 位址控制項的樣式。 套用視窗樣式的組合。 您必須包含**WS_CHILD**因為控制項必須是子視窗的樣式。 請參閱[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) Windows SDK for windows 樣式的清單中。  
  
 `rect`  
 IP 位址控制項的大小和位置參考。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構。  
  
 `pParentWnd`  
 IP 位址控制項的父視窗的指標。 它不得為**NULL。**  
  
 `nID`  
 IP 位址控制項的 id。  
  
### <a name="return-value"></a>傳回值  
 如果初始化成功，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 您建構`CIPAddressCtrl`兩個步驟中的物件。  
  
1.  呼叫建構函式，建立`CIPAddressCtrl`物件。  
  
2.  呼叫**建立**，它會建立 IP 位址控制項。  
  
 如果您想要搭配控制項使用延伸的視窗樣式，呼叫[CreateEx](#createex)而不是**建立**。  
  
##  <a name="createex"></a>CIPAddressCtrl::CreateEx  
 呼叫此函式來建立控制項 （子視窗），並將它與相關聯`CIPAddressCtrl`物件。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwExStyle`  
 指定正在建立的控制項的延伸的樣式。 如需延伸的視窗樣式的清單，請參閱`dwExStyle`參數[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) Windows SDK 中。  
  
 `dwStyle`  
 IP 位址控制項的樣式。 套用視窗樣式的組合。 您必須包含**WS_CHILD**因為控制項必須是子視窗的樣式。 請參閱[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) Windows SDK for windows 樣式的清單中。  
  
 `rect`  
 若要參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構描述的大小和位置來建立，用戶端座標中之視窗`pParentWnd`。  
  
 `pParentWnd`  
 為控制項的父視窗的指標。  
  
 `nID`  
 控制項的子視窗識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 使用`CreateEx`而不是[建立](#create)套用延伸的視窗樣式，由 Windows 擴充的樣式序言**WS_EX_**。  
  
##  <a name="getaddress"></a>CIPAddressCtrl::GetAddress  
 擷取 IP 位址控制項中的所有四個欄位的位址值。  
  
```  
int GetAddress(
    BYTE& nField0,  
    BYTE& nField1,  
    BYTE& nField2,  
    BYTE& nField3);  
  
int GetAddress(DWORD& dwAddress);
```  
  
### <a name="parameters"></a>參數  
 `nField0`  
 從壓縮的 IP 位址欄位 0 值參考。  
  
 `nField1`  
 從壓縮的 IP 位址欄位 1 值參考。  
  
 `nField2`  
 從壓縮的 IP 位址欄位 2 值參考。  
  
 `nField3`  
 從壓縮的 IP 位址欄位 3 值參考。  
  
 `dwAddress`  
 參考的位址`DWORD`接收 IP 位址的值。 請參閱**備註**顯示資料表如何`dwAddress`填滿。  
  
### <a name="return-value"></a>傳回值  
 IP 位址控制項中的非空白欄位數目。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息行為[IPM_GETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761378)、 Windows SDK 中所述。 在上述第一個原型中的數字 0 到 3 控制項的欄位中讀取由左到右分別，填入的四個參數。 在上述項目，第二個原型`dwAddress`已填入，如下所示。  
  
|欄位|包含欄位值的位元|  
|-----------|-------------------------------------|  
|0|24 到 31|  
|1|16 到 23|  
|2|8 到 15|  
|3|0 到 7|  
  
##  <a name="isblank"></a>CIPAddressCtrl::IsBlank  
 決定是否 IP 位址控制項中的所有欄位都會空白。  
  
```  
BOOL IsBlank() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果所有的 IP 位址控制項的欄位都是空的則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息行為[IPM_ISBLANK](http://msdn.microsoft.com/library/windows/desktop/bb761379)、 Windows SDK 中所述。  
  
##  <a name="setaddress"></a>CIPAddressCtrl::SetAddress  
 設定 IP 位址控制項中的所有四個欄位的位址值。  
  
```  
void SetAddress(
    BYTE nField0,  
    BYTE nField1,  
    BYTE nField2,  
    BYTE nField3);  
  
void SetAddress(DWORD dwAddress);
```  
  
### <a name="parameters"></a>參數  
 `nField0`  
 從壓縮的 IP 位址欄位 0 值。  
  
 `nField1`  
 從壓縮的 IP 位址欄位 1 值。  
  
 `nField2`  
 從壓縮的 IP 位址欄位 2 值。  
  
 `nField3`  
 從壓縮的 IP 位址欄位 3 值。  
  
 `dwAddress`  
 A`DWORD`包含新的 IP 位址的值。 請參閱**備註**的資料表，其中顯示如何`DWORD`已填入值。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息行為[IPM_SETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761380)、 Windows SDK 中所述。 在上述第一個原型中的數字 0 到 3 控制項的欄位中讀取由左到右分別，填入的四個參數。 在上述項目，第二個原型`dwAddress`已填入，如下所示。  
  
|欄位|包含欄位值的位元|  
|-----------|-------------------------------------|  
|0|24 到 31|  
|1|16 到 23|  
|2|8 到 15|  
|3|0 到 7|  
  
##  <a name="setfieldfocus"></a>CIPAddressCtrl::SetFieldFocus  
 將鍵盤焦點設定到 IP 位址控制項中的指定欄位。  
  
```  
void SetFieldFocus(WORD nField);
```  
  
### <a name="parameters"></a>參數  
 `nField`  
 以零為起始的欄位應該設定焦點的索引。 如果此值大於欄位數目，會將焦點設定為第一個空白欄位。 如果非空白的所有欄位，則會將焦點設定為第一個欄位。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息行為[IPM_SETFOCUS](http://msdn.microsoft.com/library/windows/desktop/bb761381)、 Windows SDK 中所述。  
  
##  <a name="setfieldrange"></a>CIPAddressCtrl::SetFieldRange  
 IP 位址控制項中指定之欄位中設定的範圍。  
  
```  
void SetFieldRange(
    int nField,  
    BYTE nLower,  
    BYTE nUpper);
```  
  
### <a name="parameters"></a>參數  
 `nField`  
 將套用該範圍的以零為起始的欄位索引。  
  
 `nLower`  
 在此 IP 位址控制項中接收指定之欄位的下限的整數的參考。  
  
 `nUpper`  
 在此 IP 位址控制項中接收指定之欄位的數目上限的整數的參考。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息行為[IPM_SETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761382)、 Windows SDK 中所述。 您可以使用兩個參數，`nLower`和`nUpper`，以表示的下限和上限的限制和欄位，而不是*wRange*參數搭配的 Win32 訊息。  
  
## <a name="see-also"></a>請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)



