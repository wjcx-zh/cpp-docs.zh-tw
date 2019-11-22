---
title: 命令巨集和選項巨集
description: 描述組建工具的預先定義 NMAKE 宏及其選項。
ms.date: 11/20/2019
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
no-loc:
- AS
- AFLAGS
- CC
- CFLAGS
- CPP
- CPPFLAGS
- CXX
- CXXFLAGS
- RC
- RFLAGS
- ias
- ml
- ml64
- cl
- rc
ms.openlocfilehash: d5c4477fd97e2a6c48dbac4d0ce83f7fd5f12ad6
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303173"
---
# <a name="command-macros-and-options-macros"></a>命令巨集和選項巨集

命令宏是針對 Microsoft 產品預先定義的。 Options 宏代表這些產品的選項，而且預設為未定義。 這兩者都用於預先定義的推斷規則中，而且可以用於描述區塊或使用者定義的推斷規則中。 您可以重新定義命令宏，以代表部分或所有的命令列，包括選項。 如果未定義，Options 宏會產生 null 字串。

|Microsoft 產品|命令宏|定義為|Options 宏|
|-----------------------|-------------------|----------------|-------------------|
|宏組合語言|**AS**|ml、ias 或 ml64|**AFLAGS**|
|C 編譯器|**CC**|cl|**CFLAGS**|
|C++ 編譯器|**CPP**|cl|**CPPFLAGS**|
|C++ 編譯器|**CXX**|cl|**CXXFLAGS**|
|資源編譯器|**RC**|rc|**RFLAGS**|

## <a name="see-also"></a>請參閱

[特殊的 NMAKE 巨集](special-nmake-macros.md)
