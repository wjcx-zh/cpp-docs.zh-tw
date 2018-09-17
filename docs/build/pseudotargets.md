---
title: 虛擬目標 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- makefiles, pseudotargets
- pseudotargets and NMAKE
- NMAKE program, pseudotargets
- timestamps, makefile pseudotargets
- NMAKE program, targets
ms.assetid: c8c479dc-0129-4186-8366-bc6251f2b494
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 56c0c0c93163759b604352a6e623f15726b8e7ec
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715828"
---
# <a name="pseudotargets"></a>虛擬目標

虛擬目標是用來取代在相依的檔案名稱的標籤。 它會解譯為不存在，且為已過期的檔案。 NMAKE 假設虛擬目標的時間戳記是最新的所有相依性。 如果不有任何相依項目，則會假設目前的時間。 如果虛擬目標，做為目標，一律會執行它的命令。 做為相依的虛擬目標，也必須出現為另一個相依性中的目標。 不過，該相依性不需要有命令區塊。

虛擬目標名稱遵循目標檔名語法規則。 不過，如果名稱不需要延伸模組 （也就是不包含句號），它可能會超過 8 個字元限制的檔名，它可以是最多 256 個字元。

## <a name="see-also"></a>另請參閱

[目標](../build/targets.md)