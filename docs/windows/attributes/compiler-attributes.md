---
title: 編譯器屬性 (c + + COM)
ms.date: 10/02/2018
helpviewer_keywords:
- cl.exe compiler, attributes
- attributes [C++/CLI], compiler
ms.assetid: 53cd9bee-1521-48ec-b171-80feac2096cc
ms.openlocfilehash: ea4d3119a640c0642664210384c297e011104411
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59030813"
---
# <a name="compiler-attributes"></a>編譯器屬性

編譯器屬性提供各種不同的功能。

|屬性|描述|
|---------------|-----------------|
|[emitidl](emitidl.md)|決定是否將處理並放在所產生的.idl 檔案中所有後續的 IDL 屬性。|
|[event_receiver](event-receiver.md)|建立事件接收器。|
|[event_source](event-source.md)|建立事件來源。|
|[匯出](export.md)|會導致資料結構，以放入.idl 檔案。|
|[實作](implements-cpp.md)|指定分派介面，強制讓 IDL coclass 的成員。|
|[importidl](importidl.md)|指定的.idl 檔插入所產生的.idl 檔案。|
|[importlib](importlib.md)|讓已編譯成其他類型程式庫的類型可供正在建立的類型程式庫使用。|
|[includelib](includelib-cpp.md)|會導致的.idl 或.h 檔案要包含在產生的.idl 檔案中。|
|[library_block](library-block.md)|會建構的.idl 檔案的程式庫區塊內。|
|[no_injected_text](no-injected-text.md)|防止編譯器將程式碼，因為屬性使用。|
|[satype](satype.md)|指定的資料型別`SAFEARRAY`。|
|[版本](version-cpp.md)|識別多個版本之間的介面或類別的特定版本。|

## <a name="see-also"></a>另請參閱

[依群組分類的屬性](attributes-by-group.md)