---
title: "連結器工具錯誤 LNK1256 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "xml"
  - "LNK1256"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1256"
ms.assetid: 55b64b2b-a56b-436c-a55e-ec9c6dcb050e
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 連結器工具錯誤 LNK1256
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ALINK 作業失敗：原因  
  
 LNK1256 的一個常見原因是組件的版本號碼不正確。  在組件版本號碼的任何部分中都不允許值 65535。  組件版本的有效範圍是 0 – 65534。  
  
 如果 ALINK 找不到具名的金鑰容器，也可能會造成 LNK1256。  請使用 [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md) 刪除金鑰容器並將它重新加入強式名稱 CSP。  
  
 LNK1256 的另一個原因是連結器與 Alink.dll 之間的版本不相符。  Visual Studio 安裝損毀可能會造成此問題。  請使用 Windows \[控制台\] 中的 \[程式和功能\] 來修復或重新安裝 Visual Studio。  
  
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