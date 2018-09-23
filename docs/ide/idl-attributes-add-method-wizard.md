---
title: IDL 屬性、新增方法精靈 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.method.idlattrib
dev_langs:
- C++
helpviewer_keywords:
- Add Method Wizard [C++]
- IDL attributes, Add Method Wizard
ms.assetid: f80c3bc1-b515-4d6c-83ee-98c2c21ba902
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ea2f0cd3ae445c4804738567b5bd9265363995e3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705151"
---
# <a name="idl-attributes-add-method-wizard"></a>IDL 屬性, 加入方法精靈
[新增方法精靈] 的這個頁面可用來指定方法的任何介面定義語言 (IDL) 設定。  
  
- **id**

   設定識別方法的數值識別碼。 請參閱＜MIDL 參考＞中的 [id](/windows/desktop/Midl/id)。  
  
   此方塊不適用於自訂介面，也不適用於 MFC 分配介面 (Dispinterface)。  
  
- **call_as**

   指定此區域方法可對應之遠端方法的名稱。 請參閱＜MIDL 參考＞中的 [call_as](/windows/desktop/Midl/call-as)。  
  
   不適用於 MFC 分配介面 (Dispinterface)。  
  
- **helpcontext**

   指定內容識別碼，讓使用者可在說明檔中檢視此方法的相關資訊。 請參閱＜MIDL 參考＞中的 [helpcontext](/windows/desktop/Midl/helpcontext)。  
  
   不適用於 MFC 分配介面 (Dispinterface)。  
  
- **helpstring**

   指定用來描述所套用之項目的字元字串。 根據預設，它會設定為"method <方法名稱>"。 請參閱＜MIDL 參考＞中的 [helpstring](/windows/desktop/Midl/helpstring)。  
  
   不適用於 MFC 分配介面 (Dispinterface)。  
  
- **其他屬性**

   不適用於 MFC 分配介面 (Dispinterface)。  
  
   |屬性|描述|  
   |---------------|-----------------|  
   |**hidden**|表示方法存在，但不應該在使用者導向的瀏覽器中顯示。 請參閱＜MIDL 參考＞中的 [hidden](/windows/desktop/Midl/hidden)。|  
   |**source**|表示事件來源是方法的成員。 請參閱＜MIDL 參考＞中的 [source](/windows/desktop/Midl/source)。|  
   |`local`|向 MIDL 編譯器指定方法不是遠端。 請參閱＜MIDL 參考＞中的 [local](/windows/desktop/Midl/local)。|  
   |**restricted**|指定無法任意呼叫方法。 請參閱＜MIDL 參考＞中的 [restricted](/windows/desktop/Midl/restricted)。|  
   |**vararg**|指定方法接受可變的引數數目。 若要完成這個工作，最後一個引數必須是包含所有剩餘引數的 **VARIANT** 類型安全陣列。 請參閱＜MIDL 參考＞中的 [vararg](/windows/desktop/Midl/vararg)。|  
  
## <a name="see-also"></a>請參閱  
 [新增方法](../ide/adding-a-method-visual-cpp.md)   
 [新增方法精靈](../ide/add-method-wizard.md)