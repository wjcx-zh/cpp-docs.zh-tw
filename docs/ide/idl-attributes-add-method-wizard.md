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
ms.openlocfilehash: 4a7a1e8fe89f64ad5909e7c1415545e3b3d80196
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "33337765"
---
# <a name="idl-attributes-add-method-wizard"></a>IDL 屬性, 加入方法精靈
[新增方法精靈] 的這個頁面可用來指定方法的任何介面定義語言 (IDL) 設定。  
  
 **id**  
 設定識別方法的數值識別碼。 請參閱＜MIDL 參考＞中的 [id](http://msdn.microsoft.com/library/windows/desktop/aa367040)。  
  
 此方塊不適用於自訂介面，也不適用於 MFC 分配介面 (Dispinterface)。  
  
 **call_as**  
 指定此區域方法可對應之遠端方法的名稱。 請參閱＜MIDL 參考＞中的 [call_as](http://msdn.microsoft.com/library/windows/desktop/aa366748)。  
  
 不適用於 MFC 分配介面 (Dispinterface)。  
  
 **helpcontext**  
 指定內容識別碼，讓使用者可在說明檔中檢視此方法的相關資訊。 請參閱＜MIDL 參考＞中的 [helpcontext](http://msdn.microsoft.com/library/windows/desktop/aa366851)。  
  
 不適用於 MFC 分配介面 (Dispinterface)。  
  
 **helpstring**  
 指定用來描述所套用之項目的字元字串。 根據預設，它會設定為"method <方法名稱>"。 請參閱＜MIDL 參考＞中的 [helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856)。  
  
 不適用於 MFC 分配介面 (Dispinterface)。  
  
 **其他屬性**  
 不適用於 MFC 分配介面 (Dispinterface)。  
  
|屬性|描述|  
|---------------|-----------------|  
|**hidden**|表示方法存在，但不應該在使用者導向的瀏覽器中顯示。 請參閱＜MIDL 參考＞中的 [hidden](http://msdn.microsoft.com/library/windows/desktop/aa366861)。|  
|**source**|表示事件來源是方法的成員。 請參閱＜MIDL 參考＞中的 [source](http://msdn.microsoft.com/library/windows/desktop/aa367166)。|  
|`local`|向 MIDL 編譯器指定方法不是遠端。 請參閱＜MIDL 參考＞中的 [local](http://msdn.microsoft.com/library/windows/desktop/aa367071)。|  
|**restricted**|指定無法任意呼叫方法。 請參閱＜MIDL 參考＞中的 [restricted](http://msdn.microsoft.com/library/windows/desktop/aa367157)。|  
|**vararg**|指定方法接受可變的引數數目。 若要完成這個工作，最後一個引數必須是包含所有剩餘引數的 **VARIANT** 類型安全陣列。 請參閱＜MIDL 參考＞中的 [vararg](http://msdn.microsoft.com/library/windows/desktop/aa367304)。|  
  
## <a name="see-also"></a>請參閱  
 [新增方法](../ide/adding-a-method-visual-cpp.md)   
 [新增方法精靈](../ide/add-method-wizard.md)