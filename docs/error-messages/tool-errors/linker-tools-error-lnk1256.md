---
title: 連結器工具錯誤 LNK1256 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- xml
- LNK1256
dev_langs:
- C++
helpviewer_keywords:
- LNK1256
ms.assetid: 55b64b2b-a56b-436c-a55e-ec9c6dcb050e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e4039dccb4dc8abd421b4622bbe928931f7f396
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1256"></a>連結器工具錯誤 LNK1256
ALINK 作業失敗：原因  
  
 LNK1256 的一個常見原因是組件的版本號碼不正確。 在組件版本號碼的任何部分中都不允許值 65535。 組件版本的有效範圍是 0-65534。  
  
 如果 ALINK 找不到具名的金鑰容器，也可能會造成 LNK1256。 刪除金鑰容器並將其再次加入強式名稱 CSP 使用[Sn.exe （強式名稱工具）](/dotnet/framework/tools/sn-exe-strong-name-tool)。  
  
 LNK1256 的另一個原因是連結器與 Alink.dll 之間的版本不相符。 Visual Studio 安裝損毀可能會造成此問題。 使用**程式和功能**Windows 控制台中修復或重新安裝 Visual Studio。  
  
 下列範例會產生 LNK1256：  
  
```  
// LNK1256.cpp  
// compile with: /clr /LD  
// LNK1256 expected  
[assembly:System::Reflection::AssemblyVersionAttribute("1.0.65535")];  
public class CMyClass {  
public:  
   int value;  
};  
```