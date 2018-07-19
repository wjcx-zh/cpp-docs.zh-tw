---
title: _com_ptr_t::CreateInstance |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::CreateInstance
dev_langs:
- C++
helpviewer_keywords:
- CreateInstance method [C++]
ms.assetid: ab89b0e1-9da3-4784-a079-58b17340f111
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c8aca9422c4798cd798d048ce42443c4f38bd170
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942847"
---
# <a name="comptrtcreateinstance"></a>_com_ptr_t::CreateInstance
**Microsoft 專屬**  
  
 建立指定物件的新執行個體`CLSID`或`ProgID`。  
  
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
 *rclsid*  
 `CLSID`的物件。  
  
 *clsidString*  
 Unicode 字串保存`CLSID`(開頭為"**{**") 或`ProgID`。  
  
 *clsidStringA*  
 多位元組的字串，並使用保留的 ANSI 字碼頁`CLSID`(開頭為"**{**") 或`ProgID`。  
  
 *dwClsContext*  
 執行中的可執行程式碼內容。  
  
 *pOuter*  
 外部未知[彙總](../atl/aggregation.md)。  
  
## <a name="remarks"></a>備註  
 這些成員函式會呼叫 `CoCreateInstance` 建立新的 COM 物件，然後查詢這個智慧型指標的介面類型。 然後產生的指標就會封裝在這個 `_com_ptr_t` 物件內。 `Release` 呼叫以遞減先前封裝之指標的參考計數。 此常式會傳回指出成功或失敗的 HRESULT。  
  
-   **CreateInstance (***rclsid* **，***dwClsContext***)** 會建立新的執行個體，指定的物件`CLSID`.        
  
-   **CreateInstance (***clsidString* **，***dwClsContext***)** 建立指定之物件的新執行個體Unicode 字串，其中保存`CLSID`(開頭為"**{**") 或`ProgID`。        
  
-   **CreateInstance (***clsidStringA* **，***dwClsContext***)** 建立指定之物件的新執行個體保留的多位元組字元字串`CLSID`(開頭為"**{**") 或`ProgID`。       呼叫[MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)，它會假設字串位於 ANSI 字碼頁，而不是 OEM 字碼頁。  
  
 **結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [_com_ptr_t 類別](../cpp/com-ptr-t-class.md)