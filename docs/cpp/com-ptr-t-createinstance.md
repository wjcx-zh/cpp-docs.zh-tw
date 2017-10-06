---
title: "_com_ptr_t::CreateInstance |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::CreateInstance
dev_langs:
- C++
helpviewer_keywords:
- CreateInstance method [C++]
ms.assetid: ab89b0e1-9da3-4784-a079-58b17340f111
caps.latest.revision: 6
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 1c07f7366c76c96580fc989475bd7f5ea23a38fe
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="comptrtcreateinstance"></a>_com_ptr_t::CreateInstance
**Microsoft 特定的**  
  
 建立指定物件的新執行個體**CLSID**或**ProgID**。  
  
## <a name="syntax"></a>語法  
  
```  
  
      HRESULT CreateInstance(  
   const CLSID& rclsid,  
   IUnknown* pOuter=NULL,  
   DWORD dwClsContext = CLSCTX_ALL   
) throw( );  
HRESULT CreateInstance(  
   LPCWSTR clsidString,  
   IUnknown* pOuter=NULL,  
   DWORD dwClsContext = CLSCTX_ALL   
) throw( );  
HRESULT CreateInstance(  
   LPCSTR clsidStringA,  
   IUnknown* pOuter=NULL,  
   DWORD dwClsContext = CLSCTX_ALL   
) throw( );  
```  
  
#### <a name="parameters"></a>參數  
 `rclsid`  
 **CLSID**的物件。  
  
 `clsidString`  
 保留的 Unicode 字串**CLSID** (開頭為"**{**") 或**ProgID**。  
  
 `clsidStringA`  
 多位元組字串，使用 ANSI 字碼頁，保留**CLSID** (開頭為"**{**") 或**ProgID**。  
  
 `dwClsContext`  
 執行中的可執行程式碼內容。  
  
 `pOuter`  
 外部未知[彙總](../atl/aggregation.md)。  
  
## <a name="remarks"></a>備註  
 這些成員函式會呼叫 `CoCreateInstance` 建立新的 COM 物件，然後查詢這個智慧型指標的介面類型。 然後產生的指標就會封裝在這個 `_com_ptr_t` 物件內。 **發行**呼叫以讓先前封裝之指標的參考計數遞減。 這個常式會傳回 `HRESULT`，表示成功或失敗。  
  
-   **CreateInstance (** `rclsid` **，**`dwClsContext`**)**建立新的執行執行個體的指定物件**CLSID**。        
  
-   **CreateInstance (** `clsidString` **，**`dwClsContext`**)**建立新的執行執行個體的物件指定的 Unicode 字串保留**CLSID**(開頭為"**{**") 或**ProgID**。        
  
-   **CreateInstance (** `clsidStringA` **，**`dwClsContext`**)**建立新的執行執行個體的物件，指定保留的多位元組字元字串**CLSID** (開頭為"**{**") 或**ProgID**。       呼叫[MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)，它會假設字串位於 ANSI 字碼頁，而不是 OEM 字碼頁。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_com_ptr_t 類別](../cpp/com-ptr-t-class.md)
