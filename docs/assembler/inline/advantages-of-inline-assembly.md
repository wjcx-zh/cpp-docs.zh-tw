---
title: 內嵌組譯碼的優點
ms.date: 08/30/2018
helpviewer_keywords:
- assembler [C++], advantages
- inline assembly [C++], about inline assembly
- inline assembly [C++], using
ms.assetid: 94364d97-faa7-4bdf-8473-570956986c51
ms.openlocfilehash: 7e634f78eca753487cf122ac95df55828bb64625
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169652"
---
# <a name="advantages-of-inline-assembly"></a>內嵌組譯碼的優點

**Microsoft 專屬**

因為內嵌組合不需要個別的組譯及連結步驟，所以比個別進行組譯方便。 內嵌組合語言程式碼可以使用範圍內的任何 C 變數或函式名稱，因此很容易就能與您程式的 C 程式碼整合。 因為組譯程式碼可以透過內嵌方式與 C 或 C++ 陳述式混用，因此可以執行在 C 或 C++ 中相當麻煩或無法執行的工作。

內嵌組譯碼的用法包括：

- 以組合語言撰寫函式。

- 對程式碼的速度關鍵區段進行位置最佳化。

- 讓裝置驅動程式直接存取硬體。

- 撰寫 "naked" 呼叫的初構和終解程式碼。

內嵌組譯碼是具有特殊用途的工具。 如果您打算將應用程式移植到不同的電腦上，可能會想要將電腦專屬的程式碼放在不同的模組中。 由於內嵌組譯碼並未支援全部的 Microsoft Macro Assembler (MASM) 巨集和資料指示詞，因此針對這類模組使用 MASM 可能會更方便。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[內嵌組合語言](../../assembler/inline/inline-assembler.md)<br/>
