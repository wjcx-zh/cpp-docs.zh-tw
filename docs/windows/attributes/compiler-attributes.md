---
title: 編譯器屬性（C++ COM）
ms.date: 10/02/2018
helpviewer_keywords:
- cl.exe compiler, attributes
- attributes [C++/CLI], compiler
ms.assetid: 53cd9bee-1521-48ec-b171-80feac2096cc
ms.openlocfilehash: f8eb15645049085acc047e41d0a4ea769d359871
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168275"
---
# <a name="compiler-attributes"></a>編譯器屬性

編譯器屬性提供各種功能。

|屬性|描述|
|---------------|-----------------|
|[emitidl](emitidl.md)|判斷是否要處理所有後續的 IDL 屬性，並將其放在產生的 .idl 檔案中。|
|[event_receiver](event-receiver.md)|建立事件接收器。|
|[event_source](event-source.md)|建立事件來源。|
|[export](export.md)|導致將資料結構放在 .idl 檔案中。|
|[implements](implements-cpp.md)|指定強制成為 IDL coclass 成員的分派介面。|
|[importidl](importidl.md)|將指定的 .idl 檔案插入產生的 .idl 檔案。|
|[importlib](importlib.md)|讓已編譯成其他類型程式庫的類型可供正在建立的類型程式庫使用。|
|[includelib](includelib-cpp.md)|導致 .idl 或 .h 檔案包含在產生的 .idl 檔案中。|
|[library_block](library-block.md)|將結構放在 .idl 檔案的程式庫區塊內。|
|[no_injected_text](no-injected-text.md)|防止編譯器插入程式碼做為屬性使用的結果。|
|[satype](satype.md)|指定 `SAFEARRAY`的資料類型。|
|[version](version-cpp.md)|識別介面或類別的多個版本之間的特定版本。|

## <a name="see-also"></a>另請參閱

[依群組分類的屬性](attributes-by-group.md)
