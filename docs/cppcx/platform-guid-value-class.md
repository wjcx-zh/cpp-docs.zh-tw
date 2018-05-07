---
title: 'Platform:: guid 實值類別 |Microsoft 文件'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
dev_langs:
- C++
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c295138d6239ce516b4f322fb5fc479e2235a6be
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="platformguid-value-class"></a>Platform::Guid 實值類別
代表 Windows 執行階段類型系統中的 [GUID](http://msdn.microsoft.com/library/windows/desktop/aa373931\(v=vs.85\).aspx) 類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
public value struct Guid  
```  
  
### <a name="members"></a>成員  
 GUID 具有 Equals()、GetHashCode() 和 ToString() 方法 (衍生自 [Platform::Object Class](../cppcx/platform-object-class.md))，以及 GetTypeCode() 方法 (衍生自 [Platform::Type Class](../cppcx/platform-type-class.md). Guid 也具有下列成員。  
  
|成員|描述|  
|------------|-----------------|  
|[Guid](#ctor)|初始化 Guid 結構的新執行個體。|  
|[operator==](#operator-equality)|等於運算子。|  
|[operator!=](#operator-not-equal)|不等於運算子。|  
|[operator()](#operator-call)|將 Guid 轉換成 GUID。|  
  
### <a name="remarks"></a>備註  
 如需如何使用 Windows 函式 [CoCreateGuid](http://msdn.microsoft.com/library/windows/desktop/ms688568\(v=vs.85\).aspx)產生新 Platform::Guid 的範例，請參閱 [WinRT 元件：如何產生 GUID？](http://blogs.msdn.com/b/eternalcoding/archive/2013/03/25/winrt-component-how-to-generate-a-guid.aspx)(英文)  
  
### <a name="requirements"></a>需求  
 **最低支援用戶端：** Windows 8  
  
 **最低支援伺服器：** Windows Server 2012  
  
 **命名空間：** Platform  
  
 **中繼資料：** platform.winmd  

 
## <a name="ctor"></a> Guid:: guid 建構函式
初始化 Guid 結構的新執行個體。  
  
### <a name="syntax"></a>語法  
  
```cpp  
  
    Guid(  
        unsigned int a,   
        unsigned short b,   
        unsigned short c,   
        unsigned char d,   
        unsigned char e,   
        unsigned char f,   
        unsigned char g,   
        unsigned char h,   
        unsigned char i,   
        unsigned char j,   
        unsigned char k  );  
  
    Guid(GUID m);  
  
    Guid(  
        unsigned int a,   
        unsigned short b,   
        unsigned short c,   
        Array<unsigned char>^ n );  
```  
  
### <a name="parameters"></a>參數  
 `a`  
 GUID 的前 4 個位元組。  
  
 `b`  
 GUID 接下來的 2 個位元組。  
  
 `c`  
 GUID 接下來的 2 個位元組。  
  
 `d`  
 GUID 的下一個位元組。  
  
 `e`  
 GUID 的下一個位元組。  
  
 `f`  
 GUID 的下一個位元組。  
  
 `g`  
 GUID 的下一個位元組。  
  
 `h`  
 GUID 的下一個位元組。  
  
 `i`  
 GUID 的下一個位元組。  
  
 `j`  
 GUID 的下一個位元組。  
  
 `k`  
 GUID 的下一個位元組。  
  
 `m`  
 所定義的 GUID。  
  
 `n`  
 GUID 剩餘的 8 個位元組。  
  

## <a name="operator-equality"></a> Guid::operator = = 運算子
比較兩個 guid。  
  
### <a name="syntax"></a>語法  
  
```cpp  
Platform::Guid::operator==  
```  
  
### <a name="return-value"></a>傳回值  
 如果兩個 guid 相等，則為 true。

## <a name="operator-inequality"></a> Guid::operator ！ = 運算子
比較兩個 guid。  
  
### <a name="syntax"></a>語法  
  
```cpp  
Platform::Guid::operator!=  
```  
  
### <a name="return-value"></a>傳回值  
 如果兩個 guid 是否不相等，則為 true。



## <a name="operator-call"></a> Guid 運算子
會隱含地轉換[GUID 結構](http://msdn.microsoft.com/library/windows/desktop/aa373931\(v=vs.85\).aspx)platform:: GUID。  
  
### <a name="syntax"></a>語法  
  
```cpp  
Platform::Guid operator()  
```  
  
### <a name="return-value"></a>傳回值  
 Guid 結構。  
  
  
## <a name="see-also"></a>另請參閱  
 [Platform 命名空間](../cppcx/platform-namespace-c-cx.md)