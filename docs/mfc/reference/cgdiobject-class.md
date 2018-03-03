---
title: "CGdiObject 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CGdiObject
- AFXWIN/CGdiObject
- AFXWIN/CGdiObject::CGdiObject
- AFXWIN/CGdiObject::Attach
- AFXWIN/CGdiObject::CreateStockObject
- AFXWIN/CGdiObject::DeleteObject
- AFXWIN/CGdiObject::DeleteTempMap
- AFXWIN/CGdiObject::Detach
- AFXWIN/CGdiObject::FromHandle
- AFXWIN/CGdiObject::GetObject
- AFXWIN/CGdiObject::GetObjectType
- AFXWIN/CGdiObject::GetSafeHandle
- AFXWIN/CGdiObject::UnrealizeObject
- AFXWIN/CGdiObject::m_hObject
dev_langs:
- C++
helpviewer_keywords:
- CGdiObject [MFC], CGdiObject
- CGdiObject [MFC], Attach
- CGdiObject [MFC], CreateStockObject
- CGdiObject [MFC], DeleteObject
- CGdiObject [MFC], DeleteTempMap
- CGdiObject [MFC], Detach
- CGdiObject [MFC], FromHandle
- CGdiObject [MFC], GetObject
- CGdiObject [MFC], GetObjectType
- CGdiObject [MFC], GetSafeHandle
- CGdiObject [MFC], UnrealizeObject
- CGdiObject [MFC], m_hObject
ms.assetid: 1cba3ba5-3d49-4e43-8293-209299f2f6f4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2970dddd4711c431b3809127e7eeb6f7cd3f9eb1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cgdiobject-class"></a>CGdiObject 類別
為各種 Windows 繪圖裝置介面 (GDI) 物件 (例如點陣圖、區域、筆刷、畫筆、調色盤和字型) 提供基底類別。  
  
## <a name="syntax"></a>語法  
  
```  
class CGdiObject : public CObject  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CGdiObject::CGdiObject](#cgdiobject)|建構 `CGdiObject` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CGdiObject::Attach](#attach)|將附加的 Windows GDI 物件`CGdiObject`物件。|  
|[CGdiObject::CreateStockObject](#createstockobject)|擷取其中一個 Windows 預先定義的內建畫筆、 筆刷或字型的控制代碼。|  
|[CGdiObject::DeleteObject](#deleteobject)|刪除 Windows GDI 物件附加至`CGdiObject`物件從記憶體釋出所有與物件相關聯的系統儲存體。|  
|[CGdiObject::DeleteTempMap](#deletetempmap)|刪除任何暫存`CGdiObject`所建立的物件`FromHandle`。|  
|[CGdiObject::Detach](#detach)|卸離 Windows GDI 物件，從`CGdiObject`物件，並將控制代碼傳回至 Windows GDI 物件。|  
|[CGdiObject::FromHandle](#fromhandle)|將指標傳回至`CGdiObject`物件控制代碼提供給 Windows GDI 物件。|  
|[CGdiObject::GetObject](#getobject)|填滿緩衝區的資料，描述 Windows GDI 物件附加至`CGdiObject`物件。|  
|[CGdiObject::GetObjectType](#getobjecttype)|擷取的 GDI 物件的類型。|  
|[CGdiObject::GetSafeHandle](#getsafehandle)|傳回`m_hObject`除非`this`是`NULL`的情況下`NULL`傳回。|  
|[CGdiObject::UnrealizeObject](#unrealizeobject)|重設為筆刷的原點或重設邏輯色板。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CGdiObject::operator ！ =](#operator_neq)|判斷兩個 GDI 物件是否以邏輯方式不相等。|  
|[CGdiObject::operator = =](#operator_eq_eq)|判斷兩個 GDI 物件是否等於邏輯。|  
|[CGdiObject::operator HGDIOBJ](#operator_hgdiobj)|擷取`HANDLE`附加之 Windows GDI 物件。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CGdiObject::m_hObject](#m_hobject)|A`HANDLE`包含`HBITMAP`， `HPALETTE`， `HRGN`， `HBRUSH`， `HPEN`，或`HFONT`附加至這個物件。|  
  
## <a name="remarks"></a>備註  
 您絕對不要建立`CGdiObject`直接。 相反地，您建立物件從其衍生的類別，例如`CPen`或`CBrush`。  
  
 如需有關`CGdiObject`，請參閱[圖形物件](../../mfc/graphic-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CGdiObject`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="attach"></a>CGdiObject::Attach  
 將附加的 Windows GDI 物件`CGdiObject`物件。  
  
```  
BOOL Attach(HGDIOBJ hObject);
```  
  
### <a name="parameters"></a>參數  
 `hObject`  
 A `HANDLE` Windows GDI 物件 (例如，`HPEN`或`HBRUSH`)。  
  
### <a name="return-value"></a>傳回值  
 如果附件是成功，則為非零否則便是 0。  
  
##  <a name="cgdiobject"></a>CGdiObject::CGdiObject  
 建構 `CGdiObject` 物件。  
  
```  
CGdiObject();
```  
  
### <a name="remarks"></a>備註  
 您絕對不要建立`CGdiObject`直接。 相反地，您建立物件從其衍生的類別，例如`CPen`或**Cbrush**。  
  
##  <a name="createstockobject"></a>CGdiObject::CreateStockObject  
 擷取控制代碼為其中一個預先定義的內建 Windows GDI 畫筆、 筆刷或字型，並將附加的 GDI 物件`CGdiObject`物件。  
  
```  
BOOL CreateStockObject(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 常數，指定需要的內建物件的類型。 請參閱參數*fnObject*如[GetStockObject](http://msdn.microsoft.com/library/windows/desktop/dd144925) Windows SDK 中針對適當的值的描述。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 呼叫此函式，使用其中一個衍生的類別對應至 Windows GDI 物件類型，例如`CPen`的內建的畫筆。  
  
##  <a name="deleteobject"></a>CGdiObject::DeleteObject  
 從記憶體刪除附加的 Windows GDI 物件，藉由釋放與 Windows GDI 物件相關聯的所有系統儲存體。  
  
```  
BOOL DeleteObject();
```  
  
### <a name="return-value"></a>傳回值  
 已成功刪除 GDI 物件; 如果為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 與相關聯的儲存體`CGdiObject`物件不會受到此呼叫。 應用程式不應該呼叫`DeleteObject`上`CGdiObject`放入裝置內容中目前選取的物件。  
  
 刪除模式筆刷時，不會刪除與筆刷相關聯的點陣圖。 點陣圖必須個別刪除。  
  
##  <a name="deletetempmap"></a>CGdiObject::DeleteTempMap  
 會自動呼叫`CWinApp`閒置時間處理常式，`DeleteTempMap`刪除任何暫存`CGdiObject`所建立的物件`FromHandle`。  
  
```  
static void PASCAL DeleteTempMap();
```  
  
### <a name="remarks"></a>備註  
 `DeleteTempMap`卸離 Windows GDI 物件附加至暫存`CGdiObject`物件，然後再刪除`CGdiObject`物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#175](../../mfc/codesnippet/cpp/cgdiobject-class_1.cpp)]  
  
##  <a name="detach"></a>CGdiObject::Detach  
 卸離 Windows GDI 物件，從`CGdiObject`物件，並將控制代碼傳回至 Windows GDI 物件。  
  
```  
HGDIOBJ Detach();
```  
  
### <a name="return-value"></a>傳回值  
 A`HANDLE`至 Windows GDI 物件中斷連結; 否則為**NULL**附加任何 GDI 物件。  
  
##  <a name="fromhandle"></a>CGdiObject::FromHandle  
 將指標傳回至`CGdiObject`物件控制代碼提供給 Windows GDI 物件。  
  
```  
static CGdiObject* PASCAL FromHandle(HGDIOBJ hObject);
```  
  
### <a name="parameters"></a>參數  
 `hObject`  
 A `HANDLE` Windows GDI 物件。  
  
### <a name="return-value"></a>傳回值  
 指標`CGdiObject`，可能是暫時性或永久性。  
  
### <a name="remarks"></a>備註  
 如果`CGdiObject`物件已經不附加至 Windows GDI 物件，暫時`CGdiObject`物件會建立並附加。  
  
 此暫存`CGdiObject`物件只適用於在下次應用程式在其事件迴圈中，此時就會刪除所有暫存的圖形物件有閒置時間。 另一種說法是，暫存物件的一個視窗訊息處理期間才有效。  
  
##  <a name="getobject"></a>CGdiObject::GetObject  
 填滿定義指定的物件資料緩衝區。  
  
```  
int GetObject(
    int nCount,  
    LPVOID lpObject) const;  
```  
  
### <a name="parameters"></a>參數  
 `nCount`  
 指定要複製的位元組數目`lpObject`緩衝區。  
  
 `lpObject`  
 指出使用者提供的緩衝區所接收的資訊。  
  
### <a name="return-value"></a>傳回值  
 擷取的位元組數目;否則為 0 代表發生錯誤，就會發生。  
  
### <a name="remarks"></a>備註  
 此函數會擷取資料結構，其型別取決於類型的圖形物件，如下列清單所示：  
  
|Object|緩衝區類型|  
|------------|-----------------|  
|`CPen`|[LOGPEN](../../mfc/reference/logpen-structure.md)|  
|`CBrush`|[LOGBRUSH](../../mfc/reference/logbrush-structure.md)|  
|`CFont`|[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)|  
|`CBitmap`|[點陣圖](../../mfc/reference/bitmap-structure.md)|  
|`CPalette`|**WORD**|  
|`CRgn`|不支援|  
  
 如果物件是`CBitmap`物件`GetObject`傳回僅寬度、 高度和點陣圖的色彩格式資訊。 可以使用來擷取實際的位元[CBitmap::GetBitmapBits](../../mfc/reference/cbitmap-class.md#getbitmapbits)。  
  
 如果物件是`CPalette`物件`GetObject`擷取**WORD**調色盤中指定的項目數目。 此函式不會擷取[LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040)結構，定義的調色盤。 應用程式可以藉由呼叫取得調色盤項目資訊[CPalette::GetPaletteEntries](../../mfc/reference/cpalette-class.md#getpaletteentries)。  
  
##  <a name="getobjecttype"></a>CGdiObject::GetObjectType  
 擷取的 GDI 物件的類型。  
  
```  
UINT GetObjectType() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功; 物件類型否則便是 0。 值可以是下列其中一項：  
  
- **OBJ_BITMAP**點陣圖  
  
- **OBJ_BRUSH**筆刷  
  
- **OBJ_FONT**字型  
  
- **OBJ_PAL**調色盤  
  
- **OBJ_PEN**畫筆  
  
- **OBJ_EXTPEN**擴充畫筆  
  
- **OBJ_REGION**區域  
  
- **OBJ_DC**裝置內容  
  
- **OBJ_MEMDC**記憶體裝置內容  
  
- **OBJ_METAFILE**中繼檔  
  
- **OBJ_METADC**中繼檔裝置內容  
  
- **OBJ_ENHMETAFILE**增強型中繼檔  
  
- **OBJ_ENHMETADC**增強型中繼檔裝置內容  
  
##  <a name="getsafehandle"></a>CGdiObject::GetSafeHandle  
 傳回`m_hObject`除非**這**是**NULL**的情況下**NULL**傳回。  
  
```  
HGDIOBJ GetSafeHandle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A`HANDLE`附加之 Windows GDI 物件; 否則**NULL**如果附加的物件。  
  
### <a name="remarks"></a>備註  
 這是一般的控制代碼介面架構的一部分，而且適用於**NULL**是控制代碼無效，或特殊值。  
  
### <a name="example"></a>範例  
  請參閱範例的[CWnd::IsWindowEnabled](../../mfc/reference/cwnd-class.md#iswindowenabled)。  
  
##  <a name="m_hobject"></a>CGdiObject::m_hObject  
 A`HANDLE`包含`HBITMAP`， **HRGN**， `HBRUSH`， `HPEN`， `HPALETTE`，或**HFONT**附加至這個物件。  
  
```  
HGDIOBJ m_hObject;  
```  
  
##  <a name="operator_neq"></a>CGdiObject::operator ！ =  
 判斷兩個 GDI 物件是否以邏輯方式不相等。  
  
```  
BOOL operator!=(const CGdiObject& obj) const;  
```  
  
### <a name="parameters"></a>參數  
 `obj`  
 指向現有的`CGdiObject`。  
  
### <a name="remarks"></a>備註  
 決定在左邊的 GDI 物件是否不等於右邊的 GDI 物件。  
  
##  <a name="operator_eq_eq"></a>CGdiObject::operator = =  
 判斷兩個 GDI 物件是否等於邏輯。  
  
```  
BOOL operator==(const CGdiObject& obj) const;  
```  
  
### <a name="parameters"></a>參數  
 `obj`  
 若要將現有的參考`CGdiObject`。  
  
### <a name="remarks"></a>備註  
 決定在左邊的 GDI 物件是否等於右邊的 GDI 物件。  
  
##  <a name="operator_hgdiobj"></a>CGdiObject::operator HGDIOBJ  
 擷取`HANDLE`附加之 Windows GDI 物件; 否則**NULL**如果附加的物件。  
  
```  
operator HGDIOBJ() const;  
```  
  
##  <a name="unrealizeobject"></a>CGdiObject::UnrealizeObject  
 重設為筆刷的原點或重設邏輯色板。  
  
```  
BOOL UnrealizeObject();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 雖然`UnrealizeObject`是成員函式的`CGdiObject`類別，它應叫用只在`CBrush`或`CPalette`物件。  
  
 如`CBrush`物件`UnrealizeObject`指示系統重設指定的筆刷的原點選取放入裝置內容中的下一次。 如果物件是`CPalette`物件`UnrealizeObject`指示系統要了解調色盤，就好像它有未先前已具現化。 應用程式會呼叫在下一次[CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette)函式，用於指定的調色盤，系統完全重新對應至系統調色盤邏輯色板。  
  
 `UnrealizeObject`函式不應搭配內建物件。 `UnrealizeObject`每當設定新的筆刷來源時，必須先呼叫函式 (藉由[CDC::SetBrushOrg](../../mfc/reference/cdc-class.md#setbrushorg)函式)。 `UnrealizeObject`函式不可以呼叫目前選取的筆刷或的任何顯示的內容中目前選取的調色盤。  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CBitmap 類別](../../mfc/reference/cbitmap-class.md)   
 [CBrush 類別](../../mfc/reference/cbrush-class.md)   
 [CFont 類別](../../mfc/reference/cfont-class.md)   
 [CPalette 類別](../../mfc/reference/cpalette-class.md)   
 [CPen 類別](../../mfc/reference/cpen-class.md)   
 [CRgn 類別](../../mfc/reference/crgn-class.md)
