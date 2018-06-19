---
title: 連結器工具錯誤 LNK1302 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1302
dev_langs:
- C++
helpviewer_keywords:
- LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6aa84a411f91303c84acb44e2e6c0ab3d975e19f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299415"
---
# <a name="linker-tools-error-lnk1302"></a>連結器工具錯誤 LNK1302
僅支援連結 safe .netmodule，無法連結 .netmodule 檔  
  
 .Netmodule (編譯 **/LN**) 中叫用 MSIL 連結的使用者嘗試傳遞至連結器。  C + + 模組是適用於 MSIL 連結以編譯 **/clr: safe**。  
  
 若要更正這個錯誤，編譯 **/clr: safe**啟用 MSIL 連結，或傳遞 **/clr**或 **/clr: pure** .obj 檔案，而不是模組連結器。  
  
 如需詳細資訊，請參閱  
  
-   [/LN (建立 MSIL 模組)](../../build/reference/ln-create-msil-module.md)  
  
-   [.netmodule 檔作為連結器輸入](../../build/reference/netmodule-files-as-linker-input.md)