---
title: "叫用指令碼 (ATL) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StringRegister
dev_langs:
- C++
helpviewer_keywords:
- StringRegister method
- scripts, invoking registry in ATL
ms.assetid: eabd41ee-586b-4266-9e92-5aaad04b73a4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7cbf969f601bd90e84bf0ee15ae2ea3dcb392610
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="invoking-scripts"></a>叫用指令碼
[使用可置換的參數 （登錄器的前置處理器）](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)討論取代對應，會提及的註冊機構方法**AddReplacement**。 在註冊機構有八個特定的指令碼之後，其他方法下表, 描述了所有。  
  
|方法|語法/描述|  
|------------|-------------------------|  
|**ResourceRegister**|**HRESULT ResourceRegister (LPCOLESTR***resFileName* **，UINT** `nID` **，LPCOLESTR** `szType` **);** <br /><br /> 登錄模組資源中包含的指令碼。 *resFileName*表示模組本身的 UNC 路徑。 `nID`和`szType`分別包含資源的識別碼和型別。|  
|**ResourceUnregister**|**HRESULT ResourceUnregister (LPCOLESTR***resFileName* **，UINT** `nID` **，LPCOLESTR** `szType` **);** <br /><br /> 取消註冊模組資源中包含的指令碼。 *resFileName*表示模組本身的 UNC 路徑。 `nID`和`szType`分別包含資源的識別碼和型別。|  
|**ResourceRegisterSz**|**HRESULT ResourceRegisterSz (LPCOLESTR***resFileName* **，LPCOLESTR***szID* **，LPCOLESTR** `szType` **);** <br /><br /> 登錄模組資源中包含的指令碼。 *resFileName*表示模組本身的 UNC 路徑。 *szID*和`szType`分別包含資源的字串識別項和類型。|  
|**ResourceUnregisterSz**|**HRESULT ResourceUnregisterSz (LPCOLESTR***resFileName* **，LPCOLESTR***szID* **，LPCOLESTR** `szType` **);** <br /><br /> 取消註冊模組資源中包含的指令碼。 *resFileName*表示模組本身的 UNC 路徑。 *szID*和`szType`分別包含資源的字串識別項和類型。|  
|**FileRegister**|**HRESULT FileRegister (LPCOLESTR***fileName***);** <br /><br /> 登錄的指令碼檔案中。 *檔名*是包含 （或） 的資源指令碼檔案的 UNC 路徑。|  
|**FileUnregister**|**HRESULT FileUnregister (LPCOLESTR***fileName***);** <br /><br /> 取消註冊的指令碼檔案中。 *檔名*是包含 （或） 的資源指令碼檔案的 UNC 路徑。|  
|**StringRegister**|**HRESULT StringRegister (LPCOLESTR***資料***);** <br /><br /> 在字串中登錄的指令碼。 *資料*包含指令碼本身。|  
|**StringUnregister**|**HRESULT StringUnregister (LPCOLESTR***資料***);** <br /><br /> 取消註冊在字串中的指令碼。 *資料*包含指令碼本身。|  
  
 **ResourceRegisterSz**和**ResourceUnregisterSz**，類似於**ResourceRegister**和**ResourceUnregister**，但可讓您指定字串識別項。  
  
 方法**FileRegister**和**FileUnregister**會很有用，如果您不想在資源指令碼，或您想要在其專屬檔案的指令碼。 方法**StringRegister**和**StringUnregister**讓.rgs 檔案儲存在動態配置的字串。  
  
## <a name="see-also"></a>請參閱  
 [建立登錄器指令碼](../atl/creating-registrar-scripts.md)

