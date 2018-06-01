---
title: 連結器工具錯誤 LNK1112 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1112
dev_langs:
- C++
helpviewer_keywords:
- LNK1112
ms.assetid: 425793d8-37e6-4072-9b6e-c3d4e9c12562
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 79ca2afc7270a69c443447d1b294ee7ec8bbe5a7
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704993"
---
# <a name="linker-tools-error-lnk1112"></a>連結器工具錯誤 LNK1112

> 模組電腦類型 '*type1*'與目標電腦類型的衝突'*type2*'

## <a name="remarks"></a>備註

指定輸入的目的檔被編譯成不同的電腦類型。

例如，如果您嘗試連結使用 **/clr** 編譯之目的檔，以及使用 **/clr:pure** 編譯之目的檔 (電腦類型 CEE)，連結器將會產生 LNK1112 錯誤。 **/Clr: pure**編譯器選項已被取代 Visual Studio 2015 中，在 Visual Studio 2017 中支援。

同樣地，如果您以 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 編譯器建立一個模組，也以 x86 編譯器建立另一個模組，並嘗試連結這兩者，連結器也會產生 LNK1112。

這個錯誤的可能原因是，當您開發 64 位元應用程式時，卻沒有安裝這兩個 Visual C++ 64 位元編譯器或是其中一個。 在這種情況下，就無法使用 64 位元組態。 若要修正此問題，請執行 Visual Studio 的安裝程式並安裝遺漏的 C++ 元件。

如果您在 [組態管理員]  中變更 [使用中的方案組態]  ，然後在刪除中繼專案檔之前就嘗試建置專案，也會發生這個錯誤。 若要解決這個錯誤，請從 [建置]  功能表選取 [重建方案]  。 您也可以從 [建置]  功能表選取 [清除方案]  ，然後再建置方案。

## <a name="see-also"></a>另請參閱

- [連結器工具錯誤和警告](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)
