---
title: 模組定義檔案 (.Def)
ms.date: 11/04/2016
helpviewer_keywords:
- def files
- module definition files
- .def files
ms.assetid: 08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8
ms.openlocfilehash: 0047f24722644cd9a68bbbf827ced26ad085d4c1
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812235"
---
# <a name="module-definition-def-files"></a>模組定義檔案 (.Def)

模組定義 (.def) 檔會提供連結器的匯出、 屬性和連結的程式的其他資訊的相關資訊。 建置 DLL 時，最有用的.def 檔案。 因為有[MSVC 連結器選項](linker-options.md)可用而不是模組定義陳述式，.def 檔案中通常不需要。 您也可以使用[__declspec （dllexport)](../exporting-from-a-dll-using-declspec-dllexport.md)做為指定的方式匯出的函式。

您可以使用連結器階段期間叫用.def 檔[/DEF （指定模組定義檔）](def-specify-module-definition-file.md)連結器選項。

如果您要建置沒有匯出的.exe 檔案，則使用.def 檔可讓輸出檔案較大和較慢載入。

如需範例，請參閱[DLL 使用 DEF 檔從匯出](../exporting-from-a-dll-using-def-files.md)。

請參閱下列各節，如需詳細資訊：

- [模組定義陳述式的規則](rules-for-module-definition-statements.md)

- [EXPORTS](exports.md)

- [HEAPSIZE](heapsize.md)

- [LIBRARY](library.md)

- [NAME](name-c-cpp.md)

- [區段](sections-c-cpp.md)

- [STACKSIZE](stacksize.md)

- [STUB](stub.md)

- [VERSION](version-c-cpp.md)

- [保留的字](reserved-words.md)

## <a name="see-also"></a>另請參閱

[C/C++ 建置參考](c-cpp-building-reference.md)<br/>
[MSVC 連結器選項](linker-options.md)
