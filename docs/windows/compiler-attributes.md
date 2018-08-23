---
title: 編譯器屬性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, attributes
- attributes [C++], compiler
ms.assetid: 53cd9bee-1521-48ec-b171-80feac2096cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 29c58b94293ed00ba95d4288458788a0b2edd679
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601702"
---
# <a name="compiler-attributes"></a>編譯器屬性

編譯器屬性提供各種不同的功能。

|屬性|描述|
|---------------|-----------------|
|[emitidl](../windows/emitidl.md)|決定是否將處理並放在所產生的.idl 檔案中所有後續的 IDL 屬性。|
|[event_receiver](../windows/event-receiver.md)|建立事件接收器。|
|[event_source](../windows/event-source.md)|建立事件來源。|
|[export](../windows/export.md)|會導致資料結構，以放入.idl 檔案。|
|[實作](../windows/implements-cpp.md)|指定分派介面，強制讓 IDL coclass 的成員。|
|[importidl](../windows/importidl.md)|指定的.idl 檔插入所產生的.idl 檔案。|
|[importlib](../windows/importlib.md)|讓已編譯成其他類型程式庫的類型可供正在建立的類型程式庫使用。|
|[includelib](../windows/includelib-cpp.md)|會導致的.idl 或.h 檔案要包含在產生的.idl 檔案中。|
|[library_block](../windows/library-block.md)|會建構的.idl 檔案的程式庫區塊內。|
|[no_injected_text](../windows/no-injected-text.md)|防止編譯器將程式碼，因為屬性使用。|
|[satype](../windows/satype.md)|指定的資料型別`SAFEARRAY`。|
|[version](../windows/version-cpp.md)|識別多個版本之間的介面或類別的特定版本。|

## <a name="see-also"></a>另請參閱

[依群組分類的屬性](../windows/attributes-by-group.md)