---
title: 影像格式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 3ca3654b-42fe-4253-9f2e-723644041aa0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e69d1a7c62d4e9c52cc628f30f94c346d83647f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715412"
---
# <a name="image-format"></a>映像格式

可執行映像格式是 PE32 +。 可執行映像 （Dll 和 Exe） 限於大小上限為 2 gb，因此可以用來解決靜態影像資料的 32 位元加上位移的相對位址。 此資料包含匯入位址表格，字串常數、 靜態的全域資料，以及等等。

## <a name="see-also"></a>另請參閱

[x64 軟體慣例](../build/x64-software-conventions.md)