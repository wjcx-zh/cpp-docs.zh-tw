---
title: "連結器工具錯誤 LNK1561 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1561
dev_langs:
- C++
helpviewer_keywords:
- LNK1561
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 128bd124c2536d86c8b673b54abc4b5505526b41
ms.openlocfilehash: f918c51e6f4539c020bc59ad28c867f8e2d1ae75
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---
# <a name="linker-tools-error-lnk1561"></a>連結器工具錯誤 LNK1561
必須定義進入點  
  
找不到連結器*進入點*，初始的函式呼叫中可執行檔。 根據預設，連結器會尋找`main`或`wmain`主控台應用程式中，函式`WinMain`或`wWinMain`for Windows 應用程式的函式或`DllMain`需要初始化的 dll。 您可以指定另一個函式使用[/ENTRY](../../build/reference/entry-entry-point-symbol.md)連結器選項。  
  
此錯誤有幾個原因︰  
-   您可能不包含要連結的檔案清單中定義進入點的檔案。 請確認包含進入點函式的檔案會連結到您的應用程式。  
-   您定義使用錯誤的函式簽章; 的進入點比方說，您可能有拼字錯誤或用於大小寫的函式名稱，或未正確指定傳回型別或參數型別。  
-   您可能不會指定[/DLL](../../build/reference/dll-build-a-dll.md)選項時建置 DLL。  
-   您指定可能的進入點函式名稱不正確時所使用[/ENTRY](../../build/reference/entry-entry-point-symbol.md)連結器選項。  
-   如果您使用[LIB](../../build/reference/lib-reference.md)工具來建立 DLL，請您指定一個.def 檔案。 如果是的話，移除.def 檔從組建。    
  
建置應用程式，連結器會尋找啟動您的程式碼呼叫進入點函式。 這是將應用程式載入和執行階段初始化之後呼叫的函式。 您必須提供應用程式進入點函式，或您的應用程式無法執行。 進入點是選用的 DLL。 根據預設，連結器會尋找有其中幾個特定名稱和簽章，例如進入點函式`int main(int, char**)`。 您可以指定另一個函式名稱的項目點使用 /ENTRY 連結器選項。  
  
## <a name="example"></a>範例  
 下列範例會產生 LNK1561:  
  
```cpp  
// LNK1561.cpp  
// LNK1561 expected  
int i;  
// add a main function to resolve this error  
```
