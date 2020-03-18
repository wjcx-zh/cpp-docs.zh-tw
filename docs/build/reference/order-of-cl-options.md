---
title: CL 選項的順序（C++）-Visual Studio
ms.date: 12/14/2018
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
ms.openlocfilehash: 6c57a68dd15d82a9d6a01bfe145374bda6eb1510
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439194"
---
# <a name="order-of-cl-options"></a>CL 選項的順序

選項可以出現在 CL 命令列上的任何位置，但必須最後發生的/link 選項除外。 編譯器會從[CL 環境變數](cl-environment-variables.md)中指定的選項開始，然後從左至右讀取命令列（依其遇到的連續處理命令檔）。 每個選項都適用于命令列上的所有檔案。 如果 CL 遇到衝突的選項，則會使用最右邊的選項。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
