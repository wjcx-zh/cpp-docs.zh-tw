---
title: "嚴重錯誤 C1060 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1060
dev_langs:
- C++
helpviewer_keywords:
- C1060
ms.assetid: feaf305c-c84c-4160-b974-50e283412849
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 36abe3a63515dcb3b8f07ce5d0d169329ed5f7ab
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="fatal-error-c1060"></a>嚴重錯誤 C1060
編譯器堆積空間不足  
  
 作業系統或執行階段程式庫無法滿足記憶體要求。  
  
### <a name="to-fix-this-error-try-the-following-possible-solutions"></a>若要修正這個錯誤，請嘗試下列可能的解決方案  
  
1.  如果編譯器也發出錯誤[C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md)和[C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md)，使用[/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)較低的記憶體配置上限編譯器選項。 如果您降低剩餘的記憶體配置，應用程式將有更多堆積空間可用。  
  
     如果[/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)已設定此選項，請嘗試移除它。 堆積空間可能會因為選項中指定的記憶體配置上限太高而耗盡。 編譯器會使用預設限制，如果您移除[/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)選項。  
  
2.  如果您是在 64 位元平台上編譯，請使用 64 位元編譯器工具組。 如需資訊，請參閱[How to： 啟用在命令列上的 64 位元 Visual c + + 工具組](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)。  
  
3.  在 32 位元 Windows，請嘗試使用[3 GB](http://go.microsoft.com/fwlink/?LinkId=177831) boot.ini 參數。  
  
4.  增加 Windows 交換檔的大小。  
  
5.  關閉其他正在執行的程式。  
  
6.  排除不必要的包含檔案。  
  
7.  排除不必要的全域變數，例如動態地配置記憶體，而不宣告大型陣列。  
  
8.  排除未使用到的宣告。  
  
9. 將目前的檔案分割成較小的檔案。
