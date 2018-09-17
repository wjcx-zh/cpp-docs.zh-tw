---
title: 命令巨集和選項巨集 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c66295a42fff6a2e6dde5205fb5d9139e6eceb6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705532"
---
# <a name="command-macros-and-options-macros"></a>命令巨集和選項巨集

命令巨集是預先定義的 Microsoft 產品。 選項巨集代表這些產品的選項，並預設為未定義。 同時預先定義的推斷規則中所使用，而且可以用於描述區塊或使用者定義的推斷規則。 命令巨集可以重新定義來代表部分或全部的命令列中，包括選項。 如果未定義選項巨集就會產生一個 null 字串。

|Microsoft 產品|命令巨集|定義為|選項巨集|
|-----------------------|-------------------|----------------|-------------------|
|巨集組合器|**做為**|ml|**AFLAGS**|
|基本的編譯器|**BC**|bc|**BFLAGS**|
|C 編譯器|**CC**|cl|**CFLAGS**|
|C++ 編譯器|**CPP**|cl|**CPPFLAGS**|
|C++ 編譯器|**CXX**|cl|**CXXFLAGS**|
|資源編譯器|**RC**|rc|**RFLAGS**|

## <a name="see-also"></a>另請參閱

[特殊的 NMAKE 巨集](../build/special-nmake-macros.md)