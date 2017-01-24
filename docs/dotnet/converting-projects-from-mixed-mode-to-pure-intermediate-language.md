---
title: "將專案從混合模式轉換為純中繼語言 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "中繼語言, 混合模式應用程式"
  - "混合模式應用程式"
  - "混合模式應用程式, 中繼語言"
  - "專案 [C++], 轉換為中繼語言"
ms.assetid: 855f9e3c-4f09-4bfe-8eab-a45f68292be9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 將專案從混合模式轉換為純中繼語言
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

依照預設，所有 Visual C\+\+ CLR 專案都會連結至 C 執行階段程式庫。  因此，這些專案將歸類為混合模式的應用程式，因為其將機器碼，與以 Common Language Runtime \(Managed 程式碼\) 為目標的程式碼相結合。  當編譯這些專案時，會將它們編譯成中繼語言 \(Intermediate Language，IL\)，又稱為 Microsoft Intermediate Language \(MSIL\)。  
  
### 若要將混合模式的應用程式轉換成純中繼語言  
  
1.  移除連至 [C 執行階段程式庫](../c-runtime-library/crt-library-features.md) \(CRT\) 的連結：  
  
    1.  在 .cpp 檔中定義應用程式的進入點，將進入點變更為 `Main()`。  使用 `Main()` 表示專案沒有連結至 CRT。  
  
    2.  在 \[方案總管\] 中，在專案上按一下滑鼠右鍵，然後在捷徑功能表上選取 \[**屬性**\]，以開啟應用程式的屬性頁。  
  
    3.  在 \[連結器\] 的 \[**進階**\] 專案屬性頁中，選取 \[進入點\] 欄位，然後在此欄位中輸入 **Main**。  
  
    4.  若是主控台應用程式，請在 \[連結器\] 的 \[系統\] 專案屬性頁中，選取 \[子系統\] 欄位，然後將該欄位變更為 \[主控台 \(\/SUBSYSTEM:CONSOLE\)\]。  
  
        > [!NOTE]
        >  您不需要為 Windows Form 應用程式設定此屬性，因為 \[子系統\] 欄位已預設值為 **Windows \(\/SUBSYSTEM:WINDOWS\)**。  
  
    5.  在 stdafx.h 中會將所有 `#include` 陳述式都變成註解。  例如，在主控台應用程式中：  
  
        ```  
        // #include <iostream>  
        // #include <tchar.h>  
        ```  
  
         \-或\-  
  
         例如，在 Windows Forms 應用程式：  
  
        ```  
        // #include <stdlib.h>  
        // #include <malloc.h>  
        // #include <memory.h>  
        // #include <tchar.h>  
        ```  
  
    6.  若是 Windows Form 應用程式 \(在 Form1.cpp 中\)，請將參考 windows.h 的 `#include` 陳述式標記為註解。  例如：  
  
        ```  
        // #include <windows.h>  
        ```  
  
2.  將下列程式碼加入至 stdafx.h：  
  
    ```  
    #ifndef __FLTUSED__  
    #define __FLTUSED__  
       extern "C" __declspec(selectany) int _fltused=1;  
    #endif  
    ```  
  
3.  移除所有 Unmanaged 型別：  
  
    1.  如有需要，請將 Unmanaged 型別取代成 [System](https://msdn.microsoft.com/en-us/library/system.appdomainmanager.appdomainmanager.aspx) 命名空間中之結構的參考。  下表列出幾個常見的 Managed 型別：  
  
        |結構|說明|  
        |--------|--------|  
        |[\<caps:sentence id\="tgt24" sentenceid\="84e2c64f38f78ba3ea5c905ab5a2da27" class\="tgtSentence"\>Boolean\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.boolean\(v=vs.140\).aspx)|表示布林值。|  
        |[\<caps:sentence id\="tgt26" sentenceid\="40ea57d3ee3c07bf1c102b466e1c3091" class\="tgtSentence"\>Byte\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.byte\(v=vs.140\).aspx)|表示 8 位元不帶正負號的整數 \(Unsigned Integer\)。|  
        |[\<caps:sentence id\="tgt28" sentenceid\="a87deb01c5f539e6bda34829c8ef2368" class\="tgtSentence"\>Char\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char\(v=vs.140\).aspx)|表示 Unicode 字元。|  
        |[\<caps:sentence id\="tgt30" sentenceid\="dfeaaeb4316477bd556ea5e8c3295887" class\="tgtSentence"\>DateTime\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.datetime.datetime.aspx)|表示時間的瞬間，通常以一天的日期和時間表示。|  
        |[\<caps:sentence id\="tgt32" sentenceid\="bdaa3c20a3e3851599514f7c6be5f62f" class\="tgtSentence"\>Decimal\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.decimal\(v=vs.140\).aspx)|代表十進位數值。|  
        |[\<caps:sentence id\="tgt34" sentenceid\="e8cd7da078a86726031ad64f35f5a6c0" class\="tgtSentence"\>Double\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.double\(v=vs.140\).aspx)|表示雙精度浮點數。|  
        |[\<caps:sentence id\="tgt36" sentenceid\="1e0ca5b1252f1f6b1e0ac91be7e7219e" class\="tgtSentence"\>Guid\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.guid\(v=vs.140\).aspx)|表示全域唯一識別項 \(GUID\)。|  
        |[\<caps:sentence id\="tgt38" sentenceid\="ce80d5ec65b1d2a2f1049eadc100db23" class\="tgtSentence"\>Int16\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.int16\(v=vs.140\).aspx)|表示 16 位元帶正負號的整數 \(Signed Integer\)。|  
        |[\<caps:sentence id\="tgt40" sentenceid\="0241adbbd83925f051b694d40f02747f" class\="tgtSentence"\>Int32\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.int32\(v=vs.140\).aspx)|表示 32 位元帶正負號的整數 \(Signed Integer\)。|  
        |[\<caps:sentence id\="tgt42" sentenceid\="ff9b3f96d37353c528517bc3656a00a8" class\="tgtSentence"\>Int64\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.int64\(v=vs.140\).aspx)|表示 64 位元帶正負號的整數 \(Signed Integer\)。|  
        |[\<caps:sentence id\="tgt44" sentenceid\="7f1db863563907cf33604ed7fad6b111" class\="tgtSentence"\>IntPtr\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.intptr\(v=vs.140\).aspx)|特定平台專用的型別，用來代表指標或控制代碼。|  
        |[\<caps:sentence id\="tgt46" sentenceid\="943756eb7841efcc43b7cd37d7254c76" class\="tgtSentence"\>SByte\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.byte.aspx)|代表 8 位元帶正負號的整數。|  
        |[\<caps:sentence id\="tgt48" sentenceid\="dd5c07036f2975ff4bce568b6511d3bc" class\="tgtSentence"\>Single\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.single.aspx)|表示單精確度浮點數。|  
        |[\<caps:sentence id\="tgt50" sentenceid\="90150402997ea9c8dc45cc4d41bb28cb" class\="tgtSentence"\>TimeSpan\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.timespan\(v=vs.140\).aspx)|表示時間間隔。|  
        |[\<caps:sentence id\="tgt52" sentenceid\="a00ef2ef85ff67b7b39339886f19044f" class\="tgtSentence"\>UInt16\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.uint16\(v=vs.140\).aspx)|表示 16 位元不帶正負號的整數 \(Unsigned Integer\)。|  
        |[\<caps:sentence id\="tgt54" sentenceid\="3de84ad0700f2a1571f633d399e1900e" class\="tgtSentence"\>UInt32\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.uint32\(v=vs.140\).aspx)|表示 32 位元不帶正負號的整數 \(Unsigned Integer\)。|  
        |[\<caps:sentence id\="tgt56" sentenceid\="2e8d31865e5d4b9d8611e1b991baed07" class\="tgtSentence"\>UInt64\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.uint64\(v=vs.140\).aspx)|表示 64 位元不帶正負號的整數 \(Unsigned Integer\)。|  
        |[\<caps:sentence id\="tgt58" sentenceid\="92d74abda31865424016b16e2c806a66" class\="tgtSentence"\>UIntPtr\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.uintptr\(v=vs.140\).aspx)|特定平台專用的型別，用來代表指標或控制代碼。|  
        |[\<caps:sentence id\="tgt60" sentenceid\="cab8111fd0b710a336c898e539090e34" class\="tgtSentence"\>Void\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.void\(v=vs.140\).aspx)|表示不會傳回數值的方法，也就是該方法有 void 傳回型別。|