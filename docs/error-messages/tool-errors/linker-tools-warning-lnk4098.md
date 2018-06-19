---
title: 連結器工具警告 LNK4098 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4098
dev_langs:
- C++
helpviewer_keywords:
- LNK4098
ms.assetid: 1f1b1408-1316-4e34-80f5-6a02f2db0ac1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8aadf25d968d6d457f891cab49a43591455b9d12
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301703"
---
# <a name="linker-tools-warning-lnk4098"></a>連結器工具警告 LNK4098
其他程式庫; 使用預設的程式庫 'library' 發生衝突使用 /nodefaultlib: library  
  
 您嘗試連結不相容的程式庫。  
  
> [!NOTE]
>  執行階段程式庫現在包含指示詞，以避免混用不同的型別。 相同程式中，您會收到這個警告，如果您嘗試使用不同的型別或偵錯和非偵錯版本的執行階段程式庫。 例如，如果編譯使用其中一種類型的執行階段程式庫，而另一個檔案使用的另一種 （例如，單一執行緒與多執行緒），並嘗試將它們連結至一個檔案時，您會收到這個警告。 您應該編譯所有原始程式檔使用相同的執行階段程式庫。 請參閱[使用執行階段程式庫](../../build/reference/md-mt-ld-use-run-time-library.md)(**/MD**， **/MT**， **/LD**) 編譯器選項，如需詳細資訊。  
  
 您可以使用連結器的[/verbose: lib](../../build/reference/verbose-print-progress-messages.md)參數來判斷哪些連結器搜尋的文件庫。 如果您收到 LNK4098 而想来建立可執行檔所使用，例如，單一執行緒，非偵錯執行階段程式庫，請使用 **/verbose: lib**選項，找出哪些連結器搜尋的文件庫。 連結器應該列印 LIBC.lib 和不 LIBCMT.lib、 MSVCRT.lib、 LIBCD.lib、 LIBCMTD.lib、 或 MSVCRTD.lib 作為搜尋的程式庫。 您可以告訴連結器，以忽略不正確的執行階段程式庫使用[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)您想要忽略的每個程式庫。  
  
 下表顯示您想要使用哪一個執行階段程式庫根據不應忽略哪些文件庫。  
  
|若要使用此執行階段程式庫|忽略這些程式庫|  
|-----------------------------------|----------------------------|  
|單一執行緒 (libc.lib)|libcmt.lib、 msvcrt.lib、 libcd.lib、 libcmtd.lib、 msvcrtd.lib|  
|多執行緒 (libcmt.lib)|libc.lib、 msvcrt.lib、 libcd.lib、 libcmtd.lib、 msvcrtd.lib|  
|多執行緒 DLL (msvcrt.lib) 的使用|libc.lib、 libcmt.lib、 libcd.lib、 libcmtd.lib、 msvcrtd.lib|  
|偵錯單一執行緒 (libcd.lib)|libc.lib、 libcmt.lib、 msvcrt.lib、 libcmtd.lib、 msvcrtd.lib|  
|偵錯多執行緒 (libcmtd.lib)|libc.lib、 libcmt.lib、 msvcrt.lib、 libcd.lib、 msvcrtd.lib|  
|偵錯多執行緒 DLL (msvcrtd.lib) 的使用|libc.lib、 libcmt.lib、 msvcrt.lib、 libcd.lib、 libcmtd.lib|  
  
 例如，如果您收到這個警告，而且您想要建立使用非偵錯，單一執行緒的執行階段程式庫版本的可執行檔，您可以使用下列選項，連結器：  
  
```  
/NODEFAULTLIB:libcmt.lib /NODEFAULTLIB:msvcrt.lib /NODEFAULTLIB:libcd.lib /NODEFAULTLIB:libcmtd.lib /NODEFAULTLIB:msvcrtd.lib  
```