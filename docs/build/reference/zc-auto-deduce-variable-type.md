---
title: "-Zc: auto （推算變數類型） |Microsoft 文件"
ms.custom: 
ms.date: 02/28/2018
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- /Zc:auto
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- Deduce variable type (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 5f5bc102-44c3-4688-bbe1-080594dcee5c
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 662095cdc1555891a543920a64cb7b31074914aa
ms.sourcegitcommit: eeb2b5ad8d3d22514a7b9bd7d756511b69ae0ccf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="zcauto-deduce-variable-type"></a>/Zc:auto (推算變數類型)

**/Zc: auto [-]**編譯器選項會告訴編譯器如何使用[auto 關鍵字](../../cpp/auto-keyword.md)宣告變數。 如果您指定預設選項， **/zc: auto**，編譯器會推算的類型宣告的變數，從其初始化運算式。 如果您指定**/Zc:auto-**，編譯器會自動儲存類別將變數配置。

## <a name="syntax"></a>語法

> **/Zc:auto**[**-**]  

## <a name="remarks"></a>備註

C++ 標準為 `auto` 關鍵字定義了原始和修訂的意義。 之前[!INCLUDE[cpp_dev10_long](../../build/includes/cpp_dev10_long_md.md)]，關鍵字會宣告自動儲存類別中的變數; 也就是變數具有區域存留期。 從開始[!INCLUDE[cpp_dev10_long](../../build/includes/cpp_dev10_long_md.md)]，關鍵字會推算變數，以從宣告初始化運算式的型別。 使用**/zc: auto [-]**編譯器選項，以告訴編譯器使用的原始或修訂的意義`auto`關鍵字。 **/Zc: auto**選項預設為開啟。 [/ 寬鬆-](permissive-standards-conformance.md)選項不會變更預設值為**/zc: auto**。

編譯器會發出適當的診斷訊息，如果貴用戶使用`auto`關鍵字與衝突目前**/zc: auto**編譯器選項。 如需詳細資訊，請參閱[auto 關鍵字](../../cpp/auto-keyword.md)。 如需 Visual c + + 一致性問題的詳細資訊，請參閱[非標準行為](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-visual-studio"></a>在 Visual Studio 中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取**組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 新增**/zc: auto**或**/Zc:auto-**至**其他選項：**窗格。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](../../build/reference/zc-conformance.md)<br/>
[auto 關鍵字](../../cpp/auto-keyword.md)
