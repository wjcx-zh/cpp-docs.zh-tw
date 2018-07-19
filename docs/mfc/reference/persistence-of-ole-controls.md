---
title: OLE 控制項的持續性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.ole
dev_langs:
- C++
helpviewer_keywords:
- OLE controls [MFC], persistence
- persistence, OLE controls
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 661735e91084bad45553de71e80a599afd674028
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336822"
---
# <a name="persistence-of-ole-controls"></a>OLE 控制項的持續性
OLE 控制項的其中一個功能是屬性持續性 (或序列化)，其允許 OLE 控制項對檔案或資料流來回讀取或寫入屬性值。 即使在應用程式已終結控制項之後，容器應用程式仍可以使用序列化來儲存控制項的屬性值。 當控制項的新執行個體在稍後建立時，便可以從檔案或資料流讀取 OLE 控制項的屬性值。  
  
### <a name="persistence-of-ole-controls"></a>OLE 控制項的持續性  
  
|||  
|-|-|  
|[PX_Blob](#px_blob)|交換儲存二進位大型物件 (BLOB) 資料的控制項屬性。|  
|[PX_Bool](#px_bool)|交換控制項屬性的型別**BOOL**。|  
|[PX_Color](#px_color)|交換控制項的色彩屬性。|  
|[PX_Currency](#px_currency)|交換控制項屬性的型別**CY**。|  
|[PX_DataPath](#px_datapath)|交換 `CDataPathProperty` 類型的控制項屬性。|  
|[PX_Double](#px_double)|交換控制項屬性的型別**double**。|  
|[PX_Font](#px_font)|交換控制項的字型屬性。|  
|[PX_Float](#px_float)|交換控制項屬性的型別**浮點數**。|  
|[PX_IUnknown](#px_iunknown)|交換未定義類型的控制項屬性。|  
|[PX_Long](#px_long)|交換控制項屬性的型別**長**。|  
|[PX_Picture](#px_picture)|交換控制項的圖片屬性。|  
|[PX_Short](#px_short)|交換控制項屬性的型別**簡短**。|  
|[PX_ULong](#px_ulong)|交換控制項屬性的型別**ULONG**。|  
|[PX_UShort](#px_ushort)|交換控制項屬性的型別**USHORT**。|  
|[PXstring](#px_string)|交換字元字串控制項屬性。|  
|[PX_VBXFontConvert](#px_vbxfontconvert)|交換 VBX 控制項的字型相關屬性與 OLE 控制項的字型屬性。|  
  
 颾魤 ㄛ`AfxOleTypeMatchGuid`全域函式可用來測試 TYPEDESC 與指定的 GUID 之間的相符項目。  
  
##  <a name="px_blob"></a>  PX_Blob  
 呼叫此函式內控制項的`DoPropExchange`序列化或初始化儲存二進位大型物件 (BLOB) 資料屬性的成員函式。  
  
```  
 
BOOL  
PX_Blob(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    HGLOBAL& 
hBlob  ,  
    HGLOBAL 
hBlobDefault  
= NULL);  
```  
  
### <a name="parameters"></a>參數  
 *pPX*  
 指標[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件 (通常是當做參數傳遞給`DoPropExchange`)。  
  
 *pszPropName*  
 在交換元素的屬性名稱。  
  
 *hBlob*  
 儲存屬性的變數參考 （通常是您的類別成員變數）。  
  
 *hBlobDefault*  
 屬性的預設值。  
  
### <a name="return-value"></a>傳回值  
 非零值，如果交換成功;0，如果不成功。  
  
### <a name="remarks"></a>備註  
 要讀取或寫入變數所參考的屬性值*hBlob*視需要。 此變數應該一開始呼叫之前初始化為 NULL`PX_Blob`第一次 （一般而言，這可以在控制項的建構函式）。 如果*hBlobDefault*指定，它將用於做為屬性的預設值。 如果因為任何原因而控制項的初始化及序列化程序會失敗，則會使用此值。  
  
 控制代碼*hBlob*並*hBlobDefault*記憶體區塊的其中包含下列參考：  
  
-   DWORD，其中包含二進位資料，如下所示的長度，以位元組為單位，來立即遵循  
  
-   包含實際的二進位資料的記憶體區塊。  
  
 請注意，`PX_Blob`會配置記憶體時，使用 Windows [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) API，當載入 BLOB 類型屬性。 您必須負責釋放這個記憶體。 因此，您的控制項的解構函式應該呼叫[GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579) BLOB 類型的任何屬性來釋放控制代碼會增加至您的控制項配置任何記憶體。  
  
##  <a name="px_bool"></a>  PX_Bool  
 呼叫此函式內控制項的`DoPropExchange`来序列化或 BOOL 類型的屬性初始化的成員函式。  
  
```  
 
BOOL  
PX_Bool(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    BOOL& bValue);

BOOL  
PX_Bool(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    BOOL& 
bValue  ,  
    BOOL bDefault);  
```  
  
### <a name="parameters"></a>參數  
 *pPX*  
 指標[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件 (通常是當做參數傳遞給`DoPropExchange`)。  
  
 *pszPropName*  
 在交換元素的屬性名稱。  
  
 *bValue*  
 儲存屬性的變數參考 （通常是您的類別成員變數）。  
  
 *bDefault*  
 屬性的預設值。  
  
### <a name="return-value"></a>傳回值  
 非零值，如果交換成功;0，如果不成功。  
  
### <a name="remarks"></a>備註  
 要讀取或寫入變數所參考的屬性值*bValue*視需要。 如果*bDefault*指定，它將用於做為屬性的預設值。 如果因為任何原因，控制序列化處理序失敗時，會使用此值。  
  
##  <a name="px_color"></a>  PX_Color  
 呼叫此函式內控制項的`DoPropExchange`序列化或初始化型別 OLE_COLOR 屬性的成員函式。  
  
```  
 
BOOL PX_Color(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    OLE_COLOR& clrValue);

BOOL PX_Color(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    OLE_COLOR& 
clrValue  ,  
    OLE_COLOR 
clrDefault);  
```  
  
### <a name="parameters"></a>參數  
 *pPX*  
 指標[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件 (通常是當做參數傳遞給`DoPropExchange`)。  
  
 *pszPropName*  
 在交換元素的屬性名稱。  
  
 *clrValue*  
 儲存屬性的變數參考 （通常是您的類別成員變數）。  
  
 *clrDefault*  
 控制項開發人員所定義的屬性的預設值。  
  
### <a name="return-value"></a>傳回值  
 非零值，如果交換成功;0，如果不成功。  
  
### <a name="remarks"></a>備註  
 要讀取或寫入變數所參考的屬性值*clrValue*視需要。 如果*clrDefault*指定，它將用於做為屬性的預設值。 如果因為任何原因，控制序列化處理序失敗時，會使用此值。  
  
##  <a name="px_currency"></a>  PX_Currency  
 呼叫此函式，在您的控制項`DoPropExchange`序列化或初始化型別屬性的成員函式**貨幣**。  
  
```  
 
BOOL  
PX_Currency(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CY& cyValue);

BOOL  
PX_Currency(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CY& 
cyValue  ,  
    CY cyDefault);  
```  
  
### <a name="parameters"></a>參數  
 *pPX*  
 指標[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件 (通常是當做參數傳遞給`DoPropExchange`)。  
  
 *pszPropName*  
 在交換元素的屬性名稱。  
  
 *cyValue*  
 儲存屬性的變數參考 （通常是您的類別成員變數）。  
  
 *cyDefault*  
 屬性的預設值。  
  
### <a name="return-value"></a>傳回值  
 非零值，如果交換成功;0，如果不成功。  
  
### <a name="remarks"></a>備註  
 要讀取或寫入變數所參考的屬性值*cyValue*視需要。 如果*cyDefault*指定，它將用於做為屬性的預設值。 如果因為任何原因，控制序列化處理序失敗時，會使用此值。  
  
##  <a name="px_datapath"></a>  PX_DataPath  
 呼叫此函式，在您的控制項`DoPropExchange`序列化或初始化類型的資料路徑屬性的成員函式[CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)。  
  
```  
 
BOOL  
PX_DataPath(
    CPropExchange* 
pPX,  
    LPCTSTR 
pszPropName,  
    CDataPathProperty& dataPathProperty);

BOOL  
PX_DataPath(
    CPropExchange* 
pPX,  
    CDataPathProperty& dataPathProperty);  
```  
  
### <a name="parameters"></a>參數  
 *pPX*  
 指標[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件 (通常是當做參數傳遞給`DoPropExchange`)。  
  
 *pszPropName*  
 在交換元素的屬性名稱。  
  
 *dataPathProperty*  
 儲存屬性的變數參考 （通常是您的類別成員變數）。  
  
### <a name="return-value"></a>傳回值  
 非零值，如果交換成功;0，如果不成功。  
  
### <a name="remarks"></a>備註  
 資料路徑屬性實作非同步控制項屬性。 要讀取或寫入變數所參考的屬性值*dataPathProperty*視需要。  
  
##  <a name="px_double"></a>  PX_Double  
 呼叫此函式，在您的控制項`DoPropExchange`序列化或初始化型別屬性的成員函式**double**。  
  
```  
 
BOOL  
PX_Double(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    double& doubleValue);

BOOL  
PX_Double(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    double& 
doubleValue  ,  
    double doubleDefault);  
```  
  
### <a name="parameters"></a>參數  
 *pPX*  
 指標[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件 (通常是當做參數傳遞給`DoPropExchange`)。  
  
 *pszPropName*  
 在交換元素的屬性名稱。  
  
 *doubleValue*  
 儲存屬性的變數參考 （通常是您的類別成員變數）。  
  
 *doubleDefault*  
 屬性的預設值。  
  
### <a name="return-value"></a>傳回值  
 非零值，如果交換成功;0，如果不成功。  
  
### <a name="remarks"></a>備註  
 屬性的值是讀取或寫入變數所參考*doubleValue*視需要。 如果*doubleDefault*指定，它將用於做為屬性的預設值。 如果因為任何原因，控制序列化處理序失敗時，會使用此值。  
  
##  <a name="px_font"></a>  PX_Font  
 呼叫此函式內控制項的`DoPropExchange`来序列化或 type 字型的屬性初始化的成員函式。  
  
```  
 
BOOL  
PX_Font(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CFontHolder& 
font  ,  
    const 
FONTDESC  
FAR* 
pFontDesc  
= 
NULL,  
    LPFONTDISP 
pFontDispAmbient  
= NULL);  
```  
  
### <a name="parameters"></a>參數  
 *pPX*  
 指標[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件 (通常是當做參數傳遞給`DoPropExchange`)。  
  
 *pszPropName*  
 在交換元素的屬性名稱。  
  
 *字型*  
 參考`CFontHolder`物件，包含字型屬性。  
  
 *pFontDesc*  
 指標`FONTDESC`結構，其中包含要初始化的字型屬性，在案例中的預設狀態中使用的值所在*pFontDispAmbient*是 NULL。  
  
 *pFontDispAmbient*  
 指標`IFontDisp`介面要初始化的字型屬性的預設狀態中使用的字型。  
  
### <a name="return-value"></a>傳回值  
 非零值，如果交換成功;0，如果不成功。  
  
### <a name="remarks"></a>備註  
 屬性的值是讀取或寫入`font`、`CFontHolder`參考，適當的時候。 如果*pFontDesc*並*pFontDispAmbient*指定，它們被用於初始化屬性的預設值，需要時。 如果因為任何原因，控制序列化處理序失敗時，會使用這些值。 一般而言，您傳遞 NULL 做*pFontDesc*和所傳回的環境值`COleControl::AmbientFont`如*pFontDispAmbient*。 請注意，傳回字型物件`COleControl::AmbientFont`必須藉由呼叫釋放`IFontDisp::Release`成員函式。  
  
##  <a name="px_float"></a>  PX_Float  
 呼叫此函式，在您的控制項`DoPropExchange`序列化或初始化型別屬性的成員函式**float**。  
  
```  
 
BOOL  
PX_Float(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    float& floatValue);

BOOL  
PX_Float(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    float& 
floatValue  ,  
    float floatDefault);  
```  
  
### <a name="parameters"></a>參數  
 *pPX*  
 指標[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件 (通常是當做參數傳遞給`DoPropExchange`)。  
  
 *pszPropName*  
 在交換元素的屬性名稱。  
  
 *floatValue*  
 儲存屬性的變數參考 （通常是您的類別成員變數）。  
  
 *floatDefault*  
 屬性的預設值。  
  
### <a name="return-value"></a>傳回值  
 非零值，如果交換成功;0，如果不成功。  
  
### <a name="remarks"></a>備註  
 屬性的值是讀取或寫入變數所參考*floatValue*視需要。 如果*floatDefault*指定，它將用於做為屬性的預設值。 如果因為任何原因，控制序列化處理序失敗時，會使用此值。  
  
##  <a name="px_iunknown"></a>  PX_IUnknown  
 呼叫此函式，在您的控制項`DoPropExchange`成員函式來序列化或初始化物件，而所表示的屬性`IUnknown`-衍生介面。  
  
```  
 
BOOL  
PX_IUnknown(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    LPUNKNOWN& 
pUnk  ,  
    REFIID 
iid  ,  
    LPUNKNOWN 
pUnkDefault  
= NULL);  
```  
  
### <a name="parameters"></a>參數  
 *pPX*  
 指標[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件 (通常是當做參數傳遞給`DoPropExchange`)。  
  
 *pszPropName*  
 在交換元素的屬性名稱。  
  
 *pUnk*  
 參考變數，包含表示屬性的值物件的介面。  
  
 *iid*  
 指出屬性物件的介面由控制項的介面識別碼。  
  
 *pUnkDefault*  
 屬性的預設值。  
  
### <a name="return-value"></a>傳回值  
 非零值，如果交換成功;0，如果不成功。  
  
### <a name="remarks"></a>備註  
 屬性的值是讀取或寫入變數所參考*pUnk*視需要。 如果*pUnkDefault*指定，它將用於做為屬性的預設值。 如果因為任何原因，控制序列化處理序失敗時，會使用此值。  
  
##  <a name="px_long"></a>  PX_Long  
 呼叫此函式，在您的控制項`DoPropExchange`序列化或初始化型別屬性的成員函式**長**。  
  
```  
 
BOOL  
PX_Long(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    long& lValue);

BOOL  
PX_Long(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    long& 
lValue  ,  
    long lDefault);  
```  
  
### <a name="parameters"></a>參數  
 *pPX*  
 指標[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件 (通常是當做參數傳遞給`DoPropExchange`)。  
  
 *pszPropName*  
 在交換元素的屬性名稱。  
  
 *左值*  
 儲存屬性的變數參考 （通常是您的類別成員變數）。  
  
 *lDefault*  
 屬性的預設值。  
  
### <a name="return-value"></a>傳回值  
 非零值，如果交換成功;0，如果不成功。  
  
### <a name="remarks"></a>備註  
 屬性的值是讀取或寫入變數所參考*左值*視需要。 如果*lDefault*指定，它將用於做為屬性的預設值。 如果因為任何原因，控制序列化處理序失敗時，會使用此值。  
  
##  <a name="px_picture"></a>  PX_Picture  
 呼叫此函式內控制項的`DoPropExchange`序列化或初始化您的控制項圖片屬性的成員函式。  
  
```  
 
BOOL  
PX_Picture(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CPictureHolder& pict);

BOOL  
PX_Picture(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CPictureHolder& 
pict  ,  
    CPictureHolder& pictDefault);  
```  
  
### <a name="parameters"></a>參數  
 *pPX*  
 指標[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件 (通常是當做參數傳遞給`DoPropExchange`)。  
  
 *pszPropName*  
 在交換元素的屬性名稱。  
  
 *pict*  
 若要參考[CPictureHolder](../../mfc/reference/cpictureholder-class.md)儲存屬性的物件 （通常是您的類別成員變數）。  
  
 *pictDefault*  
 屬性的預設值。  
  
### <a name="return-value"></a>傳回值  
 非零值，如果交換成功;0，如果不成功。  
  
### <a name="remarks"></a>備註  
 屬性的值是讀取或寫入變數所參考*pict*視需要。 如果*pictDefault*指定，它將用於做為屬性的預設值。 如果因為任何原因，控制序列化處理序失敗時，會使用此值。  
  
##  <a name="px_short"></a>  PX_Short  
 呼叫此函式，在您的控制項`DoPropExchange`序列化或初始化型別屬性的成員函式**簡短**。  
  
```  
 
BOOL  
PX_Short(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    short& sValue);

BOOL  
PX_Short(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    short& 
sValue  ,  
    short sDefault);  
```  
  
### <a name="parameters"></a>參數  
 *pPX*  
 指標[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件 (通常是當做參數傳遞給`DoPropExchange`)。  
  
 *pszPropName*  
 在交換元素的屬性名稱。  
  
 *sValue*  
 儲存屬性的變數參考 （通常是您的類別成員變數）。  
  
 *sDefault*  
 屬性的預設值。  
  
### <a name="return-value"></a>傳回值  
 非零值，如果交換成功;0，如果不成功。  
  
### <a name="remarks"></a>備註  
 屬性的值是讀取或寫入變數所參考*sValue*視需要。 如果*sDefault*指定，它將用於做為屬性的預設值。 如果因為任何原因，控制序列化處理序失敗時，會使用此值。  
  
##  <a name="px_ulong"></a>  PX_ULong  
 呼叫此函式，在您的控制項`DoPropExchange`序列化或初始化型別屬性的成員函式**ULONG**。  
  
```  
 
BOOL  
PX_ULong(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    ULONG& ulValue);

BOOL  
PX_ULong(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    ULONG& 
ulValue  ,  
    long ulDefault);  
```  
  
### <a name="parameters"></a>參數  
 *pPX*  
 指標[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件 (通常是當做參數傳遞給`DoPropExchange`)。  
  
 *pszPropName*  
 在交換元素的屬性名稱。  
  
 *ulValue*  
 儲存屬性的變數參考 （通常是您的類別成員變數）。  
  
 *ulDefault*  
 屬性的預設值。  
  
### <a name="return-value"></a>傳回值  
 非零值，如果交換成功;0，如果不成功。  
  
### <a name="remarks"></a>備註  
 屬性的值是讀取或寫入變數所參考*ulValue*視需要。 如果*ulDefault*指定，它將用於做為屬性的預設值。 如果因為任何原因，控制序列化處理序失敗時，會使用此值。  
  
##  <a name="px_ushort"></a>  PX_UShort  
 呼叫此函式，在您的控制項`DoPropExchange`序列化或初始化型別屬性的成員函式**unsigned short**。  
  
```  
 
BOOL  
PX_UShort(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    USHORT& usValue);

BOOL  
PX_UShort(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    USHORT& 
usValue  ,  
    USHORT usDefault);  
```  
  
### <a name="parameters"></a>參數  
 *pPX*  
 指標[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件 (通常是當做參數傳遞給`DoPropExchange`)。  
  
 *pszPropName*  
 在交換元素的屬性名稱。  
  
 *usValue*  
 儲存屬性的變數參考 （通常是您的類別成員變數）。  
  
 *usDefault*  
 屬性的預設值。  
  
### <a name="return-value"></a>傳回值  
 非零值，如果交換成功;0，如果不成功。  
  
### <a name="remarks"></a>備註  
 屬性的值是讀取或寫入變數所參考*usValue*視需要。 如果*usDefault*指定，它將用於做為屬性的預設值。 如果因為任何原因，控制序列化處理序失敗時，會使用此值。  
  
##  <a name="px_string"></a>  PXstring  
 呼叫此函式內控制項的`DoPropExchange`序列化或初始化的字元字串屬性的成員函式。  
  
```  
 
BOOL  
PXstring(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CString& strValue);

BOOL  
PXstring(
    CPropExchange* 
pPX  ,  
    LPCTSTR 
pszPropName  ,  
    CString& 
strValue  ,  
    CString strDefault);  
```  
  
### <a name="parameters"></a>參數  
 *pPX*  
 指標[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件 (通常是當做參數傳遞給`DoPropExchange`)。  
  
 *pszPropName*  
 在交換元素的屬性名稱。  
  
 *strValue*  
 儲存屬性的變數參考 （通常是您的類別成員變數）。  
  
 *strDefault*  
 屬性的預設值。  
  
### <a name="return-value"></a>傳回值  
 非零值，如果交換成功;0，如果不成功。  
  
### <a name="remarks"></a>備註  
 屬性的值是讀取或寫入變數所參考*strValue*視需要。 如果*strDefault*指定，它將用於做為屬性的預設值。 如果因為任何原因，控制序列化處理序失敗時，會使用此值。  
  
##  <a name="px_vbxfontconvert"></a>  PX_VBXFontConvert  
 呼叫此函式內控制項的`DoPropExchange`成員函式來初始化轉換 VBX 控制項的字型相關屬性的字型屬性。  
  
```  
 
BOOL  
PX_VBXFontConvert(
    CPropExchange* 
pPX  ,  
    CFontHolder& font);  
```  
  
### <a name="parameters"></a>參數  
 *pPX*  
 指標[CPropExchange](../../mfc/reference/cpropexchange-class.md)物件 (通常是當做參數傳遞給`DoPropExchange`)。  
  
 *字型*  
 將包含已轉換的 VBX 與字型相關屬性的 OLE 控制項的字型屬性。  
  
### <a name="return-value"></a>傳回值  
 非零值，如果交換成功;0，如果不成功。  
  
### <a name="remarks"></a>備註  
 此函式應僅供 OLE 控制項設計 VBX 控制項來直接取代。 當 Visual Basic 開發環境中，將轉換包含 VBX 控制項使用相對應的取代項目 OLE 控制項的表單時，它會呼叫控制項的`IDataObject::SetData`函式，並傳遞屬性集，其中包含 VBX 控制項的屬性資料。 這項作業，又會導致控制項的`DoPropExchange`要叫用的函式。 `DoPropExchange` 可以呼叫`PX_VBXFontConvert`VBX 控制項的字型相關屬性轉換 (例如，"FontName，「 fontsize 」 設，等) 的對應元件的 OLE 控制項的字型屬性。  
  
 `PX_VBXFontConvert` 應該只呼叫該控制項實際上正在轉換從 VBX 表單應用程式時。 例如:   
  
 [!code-cpp[NVC_MFCActiveXControl#14](../../mfc/codesnippet/cpp/persistence-of-ole-controls_1.cpp)]  
[!code-cpp[NVC_MFCActiveXControl#15](../../mfc/codesnippet/cpp/persistence-of-ole-controls_2.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
