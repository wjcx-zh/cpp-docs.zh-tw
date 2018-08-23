---
title: '-Zc: auto （推算變數類型） |Microsoft Docs'
ms.custom: ''
ms.date: 02/28/2018
ms.technology:
- cpp-tools
ms.topic: reference
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
ms.workload:
- cplusplus
ms.openlocfilehash: b306a104b9f71d536684e62f6dda1cac45b1d9dd
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612937"
---
# <a name="zcauto-deduce-variable-type"></a>/Zc:auto (推算變數類型)

**/Zc: auto [-]** 編譯器選項會指示編譯器使用方式[auto 關鍵字](../../cpp/auto-keyword.md)來宣告變數。 如果您指定 [預設] 選項中， **/zc: auto**，編譯器會推斷所宣告的變數，從其初始化運算式的類型。 如果您指定 **/Zc:auto-**，編譯器會自動儲存類別將變數配置。

## <a name="syntax"></a>語法

> **/Zc:auto**[**-**]  

## <a name="remarks"></a>備註

C++ 標準為 `auto` 關鍵字定義了原始和修訂的意義。 Visual c + + 2010 之前, 的關鍵字會宣告自動儲存類別; 中的變數也就是一個變數具有區域存留期。 從 Visual c + + 2010年開始，關鍵字會推斷變數，以從宣告的初始化運算式的型別。 使用  **/zc: auto [-]** 編譯器選項來告訴編譯器使用的原始或修訂的意義`auto`關鍵字。 **/Zc: auto**選項預設為開啟。 [/Permissive--](permissive-standards-conformance.md)選項不會變更預設值 **/zc: auto**。

編譯器會發出適當的診斷訊息，如果您使用`auto`關鍵字與牴觸的目前 **/zc: auto**編譯器選項。 如需詳細資訊，請參閱 < [auto 關鍵字](../../cpp/auto-keyword.md)。 如需 Visual c + + 一致性問題的詳細資訊，請參閱[非標準行為](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-visual-studio"></a>在 Visual Studio 中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 新增 **/zc: auto**或是 **/Zc:auto-** 來**其他選項：** 窗格。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](../../build/reference/zc-conformance.md)<br/>
[auto 關鍵字](../../cpp/auto-keyword.md)
