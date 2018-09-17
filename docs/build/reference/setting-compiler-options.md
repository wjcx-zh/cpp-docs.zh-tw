---
title: 設定編譯器選項 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- compiler options, setting
- cl.exe compiler, setting options
ms.assetid: 4b079f5b-0017-4124-aad6-0d2b58e427e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cf7ee185f43f62f9e9a735650801e0cbd1a1b43d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712461"
---
# <a name="setting-compiler-options"></a>設定編譯器選項

C 和 C++ 編譯器選項可以在開發環境中設定，也可以在命令列上設定。

## <a name="in-the-development-environment"></a>在開發環境中

您可以設定中每個專案的編譯器選項及其**屬性頁** 對話方塊。 在左窗格中，選取**組態屬性**， **C/c + +** ，然後選擇 編譯器選項分類。 每個編譯器選項的主題都會描述設定方式，以及各選項位於開發環境中的位置。 請參閱[編譯器選項](../../build/reference/compiler-options.md)如需完整清單。

## <a name="outside-the-development-environment"></a>在開發環境之外

您可以在下列位置設定編譯器 (CL.exe) 選項：

- [在命令列上](../../build/reference/compiler-command-line-syntax.md)

- [在 命令檔](../../build/reference/cl-command-files.md)

- [在 CL 環境變數](../../build/reference/cl-environment-variables.md)

每次叫用 CL 時，都會使用 CL 環境變數中指定的選項。 如果在 CL 環境變數或命令列中指名了某個命令檔，則會使用這個命令檔中所指定的選項。 與命令列或 CL 環境變數不同的是，命令檔可讓您使用多行選項和檔名。

編譯器選項是「由左至右」處理，而且在偵測到衝突時，會採用最後 (最右邊) 的選項。 CL 環境變數會在命令列之前處理，所以當 CL 與命令列之間發生任何衝突時，命令列具有優先權。

## <a name="additional-compiler-topics"></a>其他編譯器主題

- [快速編譯](../../build/reference/fast-compilation.md)

- [CL 叫用連結器](../../build/reference/cl-invokes-the-linker.md)

## <a name="see-also"></a>另請參閱

[C/C++ 建置參考](../../build/reference/c-cpp-building-reference.md)<br/>
[編譯器選項](../../build/reference/compiler-options.md)