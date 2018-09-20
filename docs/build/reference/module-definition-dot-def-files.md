---
title: 模組定義 (.Def) 檔 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- def files
- module definition files
- .def files
ms.assetid: 08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f04035f3c5f0acd77fc197cbef3d2ab507feb0d4
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710186"
---
# <a name="module-definition-def-files"></a>模組定義檔案 (.Def)

模組定義 (.def) 檔會提供連結器的匯出、 屬性和連結的程式的其他資訊的相關資訊。 建置 DLL 時，最有用的.def 檔案。 因為有[連結器選項](../../build/reference/linker-options.md)可用而不是模組定義陳述式，.def 檔案中通常不需要。 您也可以使用[__declspec （dllexport)](../../build/exporting-from-a-dll-using-declspec-dllexport.md)做為指定的方式匯出的函式。

您可以使用連結器階段期間叫用.def 檔[/DEF （指定模組定義檔）](../../build/reference/def-specify-module-definition-file.md)連結器選項。

如果您要建置沒有匯出的.exe 檔案，則使用.def 檔可讓輸出檔案較大和較慢載入。

如需範例，請參閱[DLL 使用 DEF 檔從匯出](../../build/exporting-from-a-dll-using-def-files.md)。

請參閱下列各節，如需詳細資訊：

- [模組定義陳述式的規則](../../build/reference/rules-for-module-definition-statements.md)

- [EXPORTS](../../build/reference/exports.md)

- [HEAPSIZE](../../build/reference/heapsize.md)

- [LIBRARY](../../build/reference/library.md)

- [名稱](../../build/reference/name-c-cpp.md)

- [區段](../../build/reference/sections-c-cpp.md)

- [STACKSIZE](../../build/reference/stacksize.md)

- [STUB](../../build/reference/stub.md)

- [版本](../../build/reference/version-c-cpp.md)

- [保留的字](../../build/reference/reserved-words.md)

## <a name="see-also"></a>另請參閱

[C/C++ 建置參考](../../build/reference/c-cpp-building-reference.md)<br/>
[連結器選項](../../build/reference/linker-options.md)