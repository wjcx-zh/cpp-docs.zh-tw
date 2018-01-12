---
title: "連結器工具警告 LNK4099 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4099
dev_langs: C++
helpviewer_keywords: LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 364c2f9303707328ebf3bdf3284398e6d4f9f0d7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4099"></a>連結器工具警告 LNK4099
PDB 'filename' 找不到與 '物件/library' 或 'path';如同沒有偵錯資訊般連結物件  
  
 連結器找不到.pdb 檔案。 將它複製到目錄，包含`object/library`。  
  
 若要尋找的物件檔案相關聯的.pdb 檔案的名稱：  
  
1.  擷取與程式庫中的物件檔案[lib](../../build/reference/lib-reference.md) **/擷取：**`objectname`**.obj** `xyz` **.lib**。  
  
2.  請檢查要使用的.pdb 檔路徑**dumpbin /section:.debug$ T /rawdata** `objectname` **.obj**。  
  
 您也可以使用編譯[/Z7](../../build/reference/z7-zi-zi-debug-information-format.md)，因此不需要使用，或者移除 pdb[偵錯](../../build/reference/debug-generate-debug-info.md)連結器選項，如果您沒有.pdb 檔案，您要連結的物件。