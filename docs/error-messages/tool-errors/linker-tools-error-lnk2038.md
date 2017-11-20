---
title: "連結器工具錯誤 LNK2038 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2038
dev_langs: C++
helpviewer_keywords: LNK2038
ms.assetid: b8d0fb35-eee6-4f52-b3c4-239cb4f65656
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 73694359c3fbcaa16455be3ce1197ba99fce56c4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk2038"></a>連結器工具錯誤 LNK2038
偵測到不相符的 '\<名稱 >': 值'\<值 1 >' 不符合值 '\<值 2 >' 中\<filename.obj >  
  
 連結器偵測到符號不相符。 這個錯誤表示應用程式的不同部分 (包括程式庫或應用程式連結到的其他目的碼) 使用符號的衝突定義。 [偵測不符](../../preprocessor/detect-mismatch.md)pragma 用來定義這類符號和偵測其衝突的值。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   在專案的目的檔過期時，會發生這個錯誤。 在您嘗試解決這個錯誤的其他方案之前，執行乾淨的組建以確保目的檔是最新的。  
  
-   Visual Studio 會定義下列符號以防止連結不相容的程式碼，此程式碼可能會造成執行階段錯誤或其他未預期的行為。  
  
     `_MSC_VER`  
     表示用來建置應用程式或程式庫的 Visual C++ 編譯器的主要和次要版本號碼。 使用其中一個版本的 Visual C++編譯器編譯的程式碼與使用主要和次要版本號碼不同的編譯器編譯的程式碼不相容。 如需詳細資訊，請參閱`_MSC_VER`中[預先定義的巨集](../../preprocessor/predefined-macros.md)。  
  
     如果您要連結到與您使用，而且您無法取得或建置相容版本的程式庫的 Visual c + + 編譯器的版本不相容的程式庫，您可以使用舊版的編譯器建置您的專案，只要變更**平台工具組**專案的屬性。 如需詳細資訊，請參閱[如何： 修改目標 Framework 和平台工具組](../../build/how-to-modify-the-target-framework-and-platform-toolset.md)。  
  
     `_ITERATOR_DEBUG_LEVEL`  
     表示在 C++ 標準程式庫中啟用的安全性層級和偵錯功能。 這些功能可以變更某些 C++ 標準程式庫物件的表示，因而使它們與使用其他安全性和偵錯功能的項目不相容。 如需詳細資訊，請參閱 [_ITERATOR_DEBUG_LEVEL](../../standard-library/iterator-debug-level.md)。  
  
     `RuntimeLibrary`  
     表示應用程式或程式庫所使用的 C++標準程式庫和 C 執行階段版本。 使用 C++ 標準程式庫或 C 執行階段某個版本的程式碼與使用不同版本的程式碼不相容。 如需詳細資訊，請參閱 [/MD、/MT、/LD (使用執行階段程式庫)](../../build/reference/md-mt-ld-use-run-time-library.md)。  
  
     `_PPLTASKS_WITH_WINRT`  
     表示會使用該程式碼[平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)連結至使用不同設定所編譯的物件[/ZW](../../build/reference/zw-windows-runtime-compilation.md)編譯器選項。 (**/ZW**支援 C + + /CX。)使用或依賴 PPL 的程式碼必須使用相同的編譯**/ZW**其餘的應用程式中使用的設定。  
  
     請確認這些符號值在您的 Visual Studio 方案的專案中一致，而且它們也與應用程式所連結的程式碼和程式庫一致。  
  
## <a name="see-also"></a>另請參閱  
 [連結器工具錯誤和警告](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)