---
title: "/Zc:externConstexpr （啟用 extern constexpr 變數） |Microsoft 文件"
ms.custom: 
ms.date: 9/29/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /Zc:externConstexpr
dev_langs: C++
helpviewer_keywords:
- -Zc:externConstexpr compiler option (C++)
- extern constexpr variables (C++)
ms.assetid: 4da5e33a-2e4d-4ed2-8616-bd8f43265c27
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 84037e5e8a942d51175d97957d0c05bd6f4aa29d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="zcexternconstexpr-enable-extern-constexpr-variables"></a>/Zc:externConstexpr （啟用 extern constexpr 變數）

**/Zc:externConstexpr**編譯器選項會告訴編譯器符合 c + + 標準，並允許的外部連結`constexpr`變數。 根據預設，Visual Studio 一律提供`constexpr`變數內部連結，即使您指定`extern`關鍵字。

## <a name="syntax"></a>語法

> /Zc:externConstexpr [-]

## <a name="remarks"></a>備註

**/Zc:externConstexpr**編譯器選項讓編譯器將適用於外部連結所宣告的變數`extern constexpr`。 **/Zc:externConstexpr**選項才可以使用 Visual Studio 2017 更新 15.5 中啟動。 在舊版的 Visual Studio，而且依預設或**/Zc:externConstexpr-**指定時，Visual Studio 會套用到內部連結`constexpr`變數，即使`extern`關鍵字使用。

如果標頭檔包含宣告的變數`extern constexpr`，它必須標示[__declspec （selectany)](../../cpp/selectany.md)才能合併連結的二進位檔中的單一執行個體重複的宣告。 否則，您可能會看到連結器錯誤，例如，發生 LNK2005，一個定義規則的違規。

### <a name="to-set-this-compiler-option-in-visual-studio"></a>在 Visual Studio 中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 在下**組態屬性**，依序展開**C/c + +** ，然後選擇 **命令列**。

1. 新增**/Zc:externConstexpr**或**/Zc:externConstexpr-**至**其他選項：**窗格。

## <a name="see-also"></a>請參閱

[/Zc （一致性）](../../build/reference/zc-conformance.md)  
[auto 關鍵字](../../cpp/auto-keyword.md)