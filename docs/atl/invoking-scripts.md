---
title: 叫用指令碼 (ATL) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- StringRegister
dev_langs:
- C++
helpviewer_keywords:
- StringRegister method
- scripts, invoking registry in ATL
ms.assetid: eabd41ee-586b-4266-9e92-5aaad04b73a4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 83baa272206bb8250e76f4e53d75b0e8a8106242
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762293"
---
# <a name="invoking-scripts"></a>叫用指令碼

[使用可置換的參數 （登錄器的前置處理器）](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)討論替代對應，提及的註冊機構方法**AddReplacement**。 註冊機構都有八個其他特定指令碼的方法，並在下表描述了所有。

|方法|語法/描述|
|------------|-------------------------|
|**ResourceRegister**|**HRESULT ResourceRegister (LPCOLESTR***resFileName* **，UINT** `nID` **，LPCOLESTR** `szType` **);**<br /><br /> 登錄模組的資源中包含的指令碼。 *resFileName*表示模組本身的 UNC 路徑。 *nID*並*szType*分別包含資源的識別碼和類型。|
|**ResourceUnregister**|**HRESULT ResourceUnregister (LPCOLESTR***resFileName* **，UINT** `nID` **，LPCOLESTR** `szType` **);**<br /><br /> 取消登錄模組的資源中包含的指令碼。 *resFileName*表示模組本身的 UNC 路徑。 *nID*並*szType*分別包含資源的識別碼和類型。|
|**ResourceRegisterSz**|**HRESULT ResourceRegisterSz (LPCOLESTR***resFileName* **，LPCOLESTR***szID* **，LPCOLESTR** `szType`**);**<br /><br /> 登錄模組的資源中包含的指令碼。 *resFileName*表示模組本身的 UNC 路徑。 *szID*並*szType*分別包含資源的字串識別項和型別。|
|**ResourceUnregisterSz**|**HRESULT ResourceUnregisterSz (LPCOLESTR***resFileName* **，LPCOLESTR***szID* **，LPCOLESTR** `szType` **);**<br /><br /> 取消登錄模組的資源中包含的指令碼。 *resFileName*表示模組本身的 UNC 路徑。 *szID*並*szType*分別包含資源的字串識別項和型別。|
|**FileRegister**|**HRESULT FileRegister (LPCOLESTR***檔名***);**<br /><br /> 註冊指令碼檔案中。 *檔名*是包含 （或） 的資源指令碼檔案的 UNC 路徑。|
|**FileUnregister**|**HRESULT FileUnregister (LPCOLESTR***檔名***);**<br /><br /> 取消註冊的指令碼檔案中。 *檔名*是包含 （或） 的資源指令碼檔案的 UNC 路徑。|
|**StringRegister**|**HRESULT StringRegister (LPCOLESTR***資料***);**<br /><br /> 註冊指令碼字串中。 *資料*包含指令碼本身。|
|**StringUnregister**|**HRESULT StringUnregister (LPCOLESTR***資料***);**<br /><br /> 取消註冊的指令碼中的字串。 *資料*包含指令碼本身。|

**ResourceRegisterSz**並**ResourceUnregisterSz**，類似於**ResourceRegister**並**ResourceUnregister**，但可讓您指定的字串識別項。

方法**FileRegister**並**FileUnregister**如果您不想在資源中的指令碼，或如果您想要自己的檔案中的指令碼是很實用。 方法**StringRegister**並**StringUnregister**讓.rgs 檔案儲存在動態配置的字串。

## <a name="see-also"></a>另請參閱

[建立登錄器指令碼](../atl/creating-registrar-scripts.md)

