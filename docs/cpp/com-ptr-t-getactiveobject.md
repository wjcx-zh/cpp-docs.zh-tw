---
title: "_com_ptr_t::GetActiveObject |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::GetActiveObject
dev_langs:
- C++
helpviewer_keywords:
- GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: a61e41c750fdf5865a475d92ba9e1def0aefd748
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="comptrtgetactiveobject"></a>_com_ptr_t::GetActiveObject
**Microsoft 特定的**  
  
 將附加至現有的執行個體的指定物件**CLSID**或**ProgID**。  
  
## <a name="syntax"></a>語法  
  
```  
  
      HRESULT GetActiveObject(  
   const CLSID& rclsid   
) throw( );  
HRESULT GetActiveObject(  
   LPCWSTR clsidString   
) throw( );  
HRESULT GetActiveObject(  
   LPCSTR clsidStringA   
) throw( );  
```  
  
#### <a name="parameters"></a>參數  
 `rclsid`  
 **CLSID**的物件。  
  
 `clsidString`  
 保留的 Unicode 字串**CLSID** (開頭為"**{**") 或**ProgID**。  
  
 `clsidStringA`  
 多位元組字串，使用 ANSI 字碼頁，保留**CLSID** (開頭為"**{**") 或**ProgID**。  
  
## <a name="remarks"></a>備註  
 這些成員函式會呼叫 `GetActiveObject` 擷取指向已向 OLE 註冊之執行中物件的指標，然後查詢這個智慧型指標的介面類型。 然後產生的指標就會封裝在這個 `_com_ptr_t` 物件內。 **發行**呼叫以讓先前封裝之指標的參考計數遞減。 這個常式會傳回 `HRESULT`，表示成功或失敗。  
  
-   **GetActiveObject (**`rclsid`**)**附加至現有的執行個體的指定物件**CLSID**。      
  
-   **GetActiveObject (**`clsidString`**)**附加至現有的執行個體的物件指定的 Unicode 字串保留**CLSID** (開頭為"**{**") 或**ProgID**。      
  
-   **GetActiveObject (**`clsidStringA`**)**附加至現有的執行個體的物件，指定保留的多位元組字元字串**CLSID** (開頭為"**{**") 或**ProgID**。     呼叫[MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)，它會假設字串位於 ANSI 字碼頁，而不是 OEM 字碼頁。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_com_ptr_t 類別](../cpp/com-ptr-t-class.md)
