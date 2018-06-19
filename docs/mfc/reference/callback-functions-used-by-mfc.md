---
title: MFC 使用的回呼函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.functions
dev_langs:
- C++
helpviewer_keywords:
- callback functions [MFC], MFC
- MFC, callback functions
- functions [MFC], callback
- callback functions [MFC]
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ce96d90506176812ffb70b580c9d95a38c65fa19
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350881"
---
# <a name="callback-functions-used-by-mfc"></a>MFC 使用的回呼函式
三個回呼函式會出現在 Mfc 程式庫。 這些回呼函式會傳遞至[cdc:: enumobjects](../../mfc/reference/cdc-class.md#enumobjects)， [cdc:: graystring](../../mfc/reference/cdc-class.md#graystring)，和[cdc:: setabortproc](../../mfc/reference/cdc-class.md#setabortproc)。 請注意，所有的回呼函式必須再傳回給 Windows，，因為無法跨回呼界限擲回例外狀況設陷 MFC 例外狀況。 如需例外狀況的詳細資訊，請參閱文章[例外狀況](../../mfc/exception-handling-in-mfc.md)。  

|名稱||  
|----------|-----------------|  
|[CDC::EnumObjects 的回呼函數](#enum_objects)||  
|[CDC::GrayString 的回呼函數](#graystring)||
|[CDC::SetAbortProc 的回呼函數](#setabortproc)|| 

## <a name="requirements"></a>需求  
 **標題:** afxwin.h 

## <a name="enum_objects"></a> Cdc:: enumobjects 的回呼函式
*ObjectFunc*名稱是應用程式提供的函式名稱的預留位置。  
  
### <a name="syntax"></a>語法  
  
```  
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,  
    LPSTR* lpData);
```  
  
### <a name="parameters"></a>參數  
 *lpszLogObject*  
 指向[LOGPEN](../../mfc/reference/logpen-structure.md)或[LOGBRUSH](../../mfc/reference/logbrush-structure.md)資料結構，其中包含之物件的邏輯屬性相關資訊。  
  
 `lpData`  
 指向傳遞至 `EnumObjects` 函式的應用程式所提供的資料。  
  
### <a name="return-value"></a>傳回值  
 回呼函式會傳回 `int`。 這個傳回的值是使用者定義的。 如果回呼函式傳回 0，`EnumObjects` 會及早停止列舉。  
  
### <a name="remarks"></a>備註  
 必須輸出實際的名稱。  
  
## <a name="graystring"></a>  Cdc:: graystring 的回呼函式
*OutputFunc*是應用程式所提供的回呼函式名稱的預留位置。  
  
### <a name="syntax"></a>語法  
  
```  
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,  
    LPARAM lpData,  
    int nCount);
```  
  
### <a name="parameters"></a>參數  
 `hDC`  
 識別記憶體裝置內容的最少為點陣圖的寬度和高度所指定`nWidth`和`nHeight`至`GrayString`。  
  
 `lpData`  
 指向要繪製的字元字串。  
  
 `nCount`  
 指定要輸出的字元數。  
  
### <a name="return-value"></a>傳回值  
 回呼函式的傳回值必須是**TRUE**表示成功; 否則就是**FALSE**。  
  
### <a name="remarks"></a>備註  
 回呼函式 (*OutputFunc*) 必須繪製影像的相對座標為 (0，0) 而非 (*x*， *y*)。  

## <a name="setabortproc"></a>  Cdc:: setabortproc 的回呼函式
名稱*AbortFunc*是應用程式提供的函式名稱的預留位置。  
  
### <a name="syntax"></a>語法  
  
```  
BOOL CALLBACK EXPORT AbortFunc(
    HDC hPr,  
    int code);
```  
  
### <a name="parameters"></a>參數  
 *hPr*  
 識別裝置內容。  
  
 `code`  
 指定是否已發生錯誤。 如果沒有發生任何錯誤，它會為 0。 它是**SP_OUTOFDISK**如果列印管理員是目前的磁碟空間不足，而且會使用應用程式會等候更多磁碟空間。 如果`code`是**SP_OUTOFDISK**，應用程式不需要中止列印工作。 如果不存在，必須產生要列印管理員呼叫**PeekMessage**或**GetMessage** Windows 函式。  
  
### <a name="return-value"></a>傳回值  
 中止處理常式函式的傳回值是如果列印的工作也會繼續執行，則為非零，0 如果被取消。  
  
### <a name="remarks"></a>備註  
 中的 < 備註 > 一節所述，必須匯出的實際名稱[cdc:: setabortproc](../../mfc/reference/cdc-class.md#setabortproc)。  
 
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](structures-styles-callbacks-and-message-maps.md) [cdc:: enumobjects](../../mfc/reference/cdc-class.md#enumobjects) [cdc:: setabortproc](../../mfc/reference/cdc-class.md#setabortproc) [cdc:: graystring](../../mfc/reference/cdc-class.md#graystring)

