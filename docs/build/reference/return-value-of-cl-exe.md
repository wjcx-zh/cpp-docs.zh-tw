---
title: Cl.exe 的傳回值 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, return value
ms.assetid: 7c2d7f33-ee0d-4199-8ef4-75fe2b007670
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc8b5deab86597aca6e35b3d6f2d1adcca18be69
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374589"
---
# <a name="return-value-of-clexe"></a>cl.exe 的傳回值
cl.exe 傳回零，代表成功 (沒有錯誤)，否則即傳回非零。  
  
 如果您是從指令碼、powershell、.cmd 或 .bat 檔案進行編譯，cl.exe 的傳回值會很實用。 建議您擷取編譯器的輸出，萬一發生錯誤或警告，就可加以解決。  
  
 cl.exe 有太多可能的錯誤結束代碼，無法全部列出。 您可以查閱錯誤碼中的 winerror.h 或 ntstatus.h 檔案中 Windows 軟體開發套件，在 %programfiles (x86) %\Windows 套件內含\\`version`\Include\shared\ 目錄。 以十進位格式傳回的錯誤碼必須轉換成十六進位才能進行搜尋。 例如，錯誤碼 -1073741620 轉換為十六進位會是 0xC00000CC。 這個錯誤是在 ntstatus.h 中找到，對應的訊息為「遠端伺服器上找不到指定的共用名稱」(The specified share name cannot be found on the remote server)。 如需可下載的 Windows 錯誤碼清單，請參閱[ &#91;MS ERREF&#93;: Windows 錯誤碼](http://msdn.microsoft.com/library/cc231196)。  
  
 您也可以使用 Visual Studio 中的錯誤查詢公用程式，找出編譯器錯誤訊息代表的意義。 在 Visual Studio 命令殼層中輸入**errlook.exe**啟動公用程式，或在 Visual Studio IDE 中，功能表列上選擇**工具**，**錯誤查閱**。 輸入錯誤值，就可以找到與錯誤相關聯的描述文字。 如需詳細資訊，請參閱[ERRLOOK 參考](../../build/reference/errlook-reference.md)。  
  
## <a name="remarks"></a>備註  
 以下範例 .bat 檔是使用 cl.exe 的傳回值。  
  
```  
echo off  
cl /W4 t.cpp  
@if ERRORLEVEL == 0 (  
   goto good  
)  
  
@if ERRORLEVEL != 0 (  
   goto bad  
)  
  
:good  
   echo "clean compile"  
   echo %ERRORLEVEL%  
   goto end  
  
:bad  
   echo "error or warning"  
   echo %ERRORLEVEL%  
   goto end  
  
:end  
```  
  
## <a name="see-also"></a>另請參閱  
 [編譯器命令列語法](../../build/reference/compiler-command-line-syntax.md)