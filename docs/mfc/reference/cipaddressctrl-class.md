---
title: "CIPAddressCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CIPAddressCtrl
dev_langs:
- C++
helpviewer_keywords:
- IP address control
- Internet address edit box
- CIPAddressCtrl class
- Internet protocol address box
- common controls, Internet Explorer 4.0
- Internet Explorer 4.0 common controls
ms.assetid: 9764d2f4-cb14-4ba8-b799-7f57a55a47c6
caps.latest.revision: 22
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
ms.openlocfilehash: b3849580c7bfd07f241e55cc48144959566d7d09
ms.lasthandoff: 02/24/2017

---
# <a name="cipaddressctrl-class"></a>CIPAddressCtrl 類別
提供 Windows 通用 IP 位址控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CIPAddressCtrl : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CIPAddressCtrl::CIPAddressCtrl](#cipaddressctrl)|建構 `CIPAddressCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CIPAddressCtrl::ClearAddress](#clearaddress)|清除 IP 位址控制項的內容。|  
|[CIPAddressCtrl::Create](#create)|建立 IP 位址控制項並將它附加`CIPAddressCtrl`物件。|  
|[CIPAddressCtrl::CreateEx](#createex)|建立具有指定的 Windows 延伸樣式的 IP 位址控制項，並將其以附加`CIPAddressCtrl`物件。|  
|[CIPAddressCtrl::GetAddress](#getaddress)|擷取 IP 位址控制項中的所有四個欄位的位址值。|  
|[CIPAddressCtrl::IsBlank](#isblank)|決定是否 IP 位址控制項中的所有欄位都會空白。|  
|[CIPAddressCtrl::SetAddress](#setaddress)|設定 IP 位址控制項中的所有四個欄位的位址值。|  
|[CIPAddressCtrl::SetFieldFocus](#setfieldfocus)|將鍵盤焦點設定為在 IP 位址控制項中指定的欄位。|  
|[CIPAddressCtrl::SetFieldRange](#setfieldrange)|設定範圍中 IP 位址控制項的指定欄位。|  
  
## <a name="remarks"></a>備註  
 IP 位址控制項，類似於編輯控制項，控制項可讓您輸入和管理網際網路通訊協定 (IP) 格式的數字位址。  
  
 這個控制項 (並因此`CIPAddressCtrl`類別) 僅適用於執行在 Microsoft Internet Explorer 4.0 及更新版本的程式。 它們也會出現在未來版本的 Windows 和 Windows NT。  
  
 一般 IP 位址控制項的詳細資訊，請參閱[IP 位址控制項](http://msdn.microsoft.com/library/windows/desktop/bb761372)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CIPAddressCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
##  <a name="a-namecipaddressctrla--cipaddressctrlcipaddressctrl"></a><a name="cipaddressctrl"></a>CIPAddressCtrl::CIPAddressCtrl  
 建立 `CIPAddressCtrl` 物件。  
  
```  
CIPAddressCtrl();
```  
  
##  <a name="a-nameclearaddressa--cipaddressctrlclearaddress"></a><a name="clearaddress"></a>CIPAddressCtrl::ClearAddress  
 清除 IP 位址控制項的內容。  
  
```  
void ClearAddress();
```  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[IPM_CLEARADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761377)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namecreatea--cipaddressctrlcreate"></a><a name="create"></a>CIPAddressCtrl::Create  
 建立 IP 位址控制項並將它附加`CIPAddressCtrl`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 IP 位址控制項的樣式。 套用的視窗樣式的組合。 您必須包含**WS_CHILD**因為控制項必須是子視窗的樣式。 請參閱[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的視窗樣式清單。  
  
 `rect`  
 IP 位址控制項的大小和位置參考。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構。  
  
 `pParentWnd`  
 IP 位址控制項的父視窗的指標。 它不得為**NULL。**  
  
 `nID`  
 IP 位址控制項的 id。  
  
### <a name="return-value"></a>傳回值  
 如果初始化成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 您建構`CIPAddressCtrl`兩個步驟中的物件。  
  
1.  呼叫建構函式，建立`CIPAddressCtrl`物件。  
  
2.  呼叫**建立**，這樣就可以建立 IP 位址控制項。  
  
 如果您想要使用延伸的視窗樣式與您的控制項，呼叫[CreateEx](#createex)而不是**建立**。  
  
##  <a name="a-namecreateexa--cipaddressctrlcreateex"></a><a name="createex"></a>CIPAddressCtrl::CreateEx  
 呼叫此函式可建立的控制項 （子視窗），並將它與關聯`CIPAddressCtrl`物件。  
  
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
 指定正在建立的控制項的延伸的樣式。 如需延伸視窗樣式，請參閱`dwExStyle`參數[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwStyle`  
 IP 位址控制項的樣式。 套用的視窗樣式的組合。 您必須包含**WS_CHILD**因為控制項必須是子視窗的樣式。 請參閱[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的視窗樣式清單。  
  
 `rect`  
 參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構描述的大小和位置來建立、 用戶端座標中的視窗的`pParentWnd`。  
  
 `pParentWnd`  
 是控制項的父視窗的指標。  
  
 `nID`  
 控制項的子視窗的 id。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 使用`CreateEx`而不是[建立](#create)套用延伸的視窗樣式，指定 Windows 延伸的樣式序言**WS_EX_**。  
  
##  <a name="a-namegetaddressa--cipaddressctrlgetaddress"></a><a name="getaddress"></a>CIPAddressCtrl::GetAddress  
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
 此成員函式實作的 Win32 訊息的行為[IPM_GETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761378)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 在上述第一個原型中的數字 0 到 3 的控制項欄位讀取左到右分別，填入四個參數。 在上述第二個原型`dwAddress`已填入，如下所示。  
  
|欄位|包含欄位值的位元|  
|-----------|-------------------------------------|  
|0|24 到 31|  
|1|16 到 23|  
|2|8 到 15|  
|3|0 到 7|  
  
##  <a name="a-nameisblanka--cipaddressctrlisblank"></a><a name="isblank"></a>CIPAddressCtrl::IsBlank  
 決定是否 IP 位址控制項中的所有欄位都會空白。  
  
```  
BOOL IsBlank() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果要將所有 IP 位址控制項的欄位是空的。否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[IPM_ISBLANK](http://msdn.microsoft.com/library/windows/desktop/bb761379)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetaddressa--cipaddressctrlsetaddress"></a><a name="setaddress"></a>CIPAddressCtrl::SetAddress  
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
 A`DWORD`值，其中包含新的 IP 位址。 請參閱**備註**顯示資料表如何`DWORD`已填入值。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[IPM_SETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761380)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 在上述第一個原型中的數字 0 到 3 的控制項欄位讀取左到右分別，填入四個參數。 在上述第二個原型`dwAddress`已填入，如下所示。  
  
|欄位|包含欄位值的位元|  
|-----------|-------------------------------------|  
|0|24 到 31|  
|1|16 到 23|  
|2|8 到 15|  
|3|0 到 7|  
  
##  <a name="a-namesetfieldfocusa--cipaddressctrlsetfieldfocus"></a><a name="setfieldfocus"></a>CIPAddressCtrl::SetFieldFocus  
 將鍵盤焦點設定為在 IP 位址控制項中指定的欄位。  
  
```  
void SetFieldFocus(WORD nField);
```  
  
### <a name="parameters"></a>參數  
 `nField`  
 應該設定焦點的以零為起始的欄位索引。 如果此值大於欄位數目，焦點設為第一個空白欄位。 如果所有欄位都均非空白，焦點設為第一個欄位。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[IPM_SETFOCUS](http://msdn.microsoft.com/library/windows/desktop/bb761381)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetfieldrangea--cipaddressctrlsetfieldrange"></a><a name="setfieldrange"></a>CIPAddressCtrl::SetFieldRange  
 設定範圍中 IP 位址控制項的指定欄位。  
  
```  
void SetFieldRange(
    int nField,  
    BYTE nLower,  
    BYTE nUpper);
```  
  
### <a name="parameters"></a>參數  
 `nField`  
 將會套用該範圍的以零為起始的欄位索引。  
  
 `nLower`  
 在此 IP 位址控制項接收指定之欄位的下限的整數的參考。  
  
 `nUpper`  
 在此 IP 位址控制項接收指定的欄位數上限的整數的參考。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[IPM_SETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761382)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 您可以使用兩個參數，`nLower`和`nUpper`，以表示的下限和上限的限制和欄位，而不是*wRange*的 Win32 訊息搭配使用的參數。  
  
## <a name="see-also"></a>另請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)




