---
title: -APPCONTAINER |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /APPCONTAINER
dev_langs:
- C++
helpviewer_keywords:
- APPCONTAINER editbin option
- -APPCONTAINER editbin option
- /APPCONTAINER editbin option
ms.assetid: 0ca4f1ec-c8de-4a37-b3e2-deda7af0bb88
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ea6f08a141d48183d96dba6cb02fcf31909af0ae
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43686249"
---
# <a name="appcontainer"></a>/APPCONTAINER
標記必須在應用程式容器中執行的可執行檔 — 比方說，Microsoft Store 或通用 Windows 應用程式。  
  
```  
  
/APPCONTAINER[:NO]  
```  
  
## <a name="remarks"></a>備註  
 已設定 **/APPCONTAINER** 選項的可執行檔只能在應用程式容器中執行，這是在 Windows 8 中引進的處理序隔離環境。 Microsoft Store 和通用 Windows 應用程式，必須設定這個選項。  
  
## <a name="see-also"></a>另請參閱  
 [EDITBIN 選項](../../build/reference/editbin-options.md)   
 [什麼是通用 Windows 應用程式？](/windows/uwp/get-started/universal-application-platform-guide)