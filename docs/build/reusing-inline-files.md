---
title: 重複使用內嵌檔 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline files, reusing NMAKE
- revising inline files
- NMAKE program, inline files
ms.assetid: d42dbffb-2cef-4ccb-9a1f-20b8ef81481c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 37544db8076d40e638b6ddf6f340070298229149
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722458"
---
# <a name="reusing-inline-files"></a>重複使用內嵌檔

若要重複使用 inline 檔，請指定 <<*檔名*其中定義檔案，且第一次使用，然後重複使用*filename*而不需要 << 稍後相同或不同的命令。 建立內嵌檔案的命令必須先執行才能使用檔案的所有命令。

## <a name="see-also"></a>另請參閱

[Makefile 中的內嵌檔](../build/inline-files-in-a-makefile.md)