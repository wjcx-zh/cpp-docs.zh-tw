---
title: _com_ptr_t::GetActiveObject |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::GetActiveObject
dev_langs:
- C++
helpviewer_keywords:
- GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 392460cde35096bc1c61db4d7e6bd2143932838d
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39403991"
---
# <a name="comptrtgetactiveobject"></a>_com_ptr_t::GetActiveObject
**Microsoft 專屬**  
  
 將附加至現有的執行個體的物件的給定`CLSID`或`ProgID`。  
  
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
 *rclsid*  
 `CLSID`的物件。  
  
 *clsidString*  
 Unicode 字串保存`CLSID`(開頭為"**{**") 或`ProgID`。  
  
 *clsidStringA*  
 多位元組的字串，並使用保留的 ANSI 字碼頁`CLSID`(開頭為"**{**") 或`ProgID`。  
  
## <a name="remarks"></a>備註  
 這些成員函式呼叫**GetActiveObject**擷取已向 OLE 執行物件的指標，然後查詢這個智慧型指標的介面類型。 然後產生的指標就會封裝在這個 `_com_ptr_t` 物件內。 `Release` 呼叫以遞減先前封裝之指標的參考計數。 此常式會傳回指出成功或失敗的 HRESULT。  
  
-   **GetActiveObject (**`rclsid`**)** 附加至現有的執行個體的指定物件`CLSID`。  
  
-   **GetActiveObject (**`clsidString`**)** 附加至現有的執行個體的物件指定的 Unicode 字串保存`CLSID`(開頭為"**{**") 或`ProgID`.  
  
-   **GetActiveObject (**`clsidStringA`**)** 附加至現有的執行個體的物件，指定保留的多位元組字元字串`CLSID`(開頭為"**{**") 或`ProgID`. 呼叫[MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)，它會假設字串位於 ANSI 字碼頁，而不是 OEM 字碼頁。  
  
 **結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [_com_ptr_t 類別](../cpp/com-ptr-t-class.md)