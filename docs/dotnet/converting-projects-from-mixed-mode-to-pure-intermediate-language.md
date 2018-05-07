---
title: 轉換專案從混合模式為純中繼語言 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- intermediate language, mixed-mode applications
- mixed-mode applications
- mixed-mode applications, intermediate language
- projects [C++], converting to intermediate language
ms.assetid: 855f9e3c-4f09-4bfe-8eab-a45f68292be9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ad39f7943effdea8029390971071724bf2294bdf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="converting-projects-from-mixed-mode-to-pure-intermediate-language"></a>將專案從混合模式轉換為純中繼語言
根據預設，所有的 Visual c + + CLR 專案連結至 C 執行階段程式庫的。 因此，這些專案分類為混合模式應用程式，因為 common language runtime （managed 程式碼） 為目標的程式碼與原生程式碼結合。 在編譯時就會編譯成中繼語言 (IL)，也稱為 Microsoft intermediate language (MSIL)。  
  
### <a name="to-convert-your-mixed-mode-application-into-pure-intermediate-language"></a>若要將您的混合模式應用程式轉換成純中繼語言  
  
1.  移除連結[C 執行階段程式庫](../c-runtime-library/crt-library-features.md)(CRT):  
  
    1.  在.cpp 檔案中定義您的應用程式的進入點變更的進入點`Main()`。 使用`Main()`指出您的專案未連結到 CRT 的資訊。  
  
    2.  在 [方案總管] 中，以滑鼠右鍵按一下您的專案，然後選取**屬性**快顯功能表，開啟您的應用程式的屬性頁上。  
  
    3.  在**進階**專案屬性頁**連結器**，選取**進入點**，然後輸入**Main**此欄位中。  
  
    4.  主控台應用程式，在**系統**專案屬性頁**連結器**，選取**子系統**欄位，然後將這變更為**主控台 （/SUBSYSTEM:CONSOLE)**。  
  
        > [!NOTE]
        >  您沒有設定這個屬性，Windows Forms 應用程式，因為**子系統**欄位設定為**Windows (/ 子系統： WINDOWS)** 預設。  
  
    5.  在 stdafx.h，標記為註解所有`#include`陳述式。 例如，在主控台應用程式：  
  
        ```  
        // #include <iostream>  
        // #include <tchar.h>  
        ```  
  
         -或-  
  
         例如，在 Windows Form 應用程式：  
  
        ```  
        // #include <stdlib.h>  
        // #include <malloc.h>  
        // #include <memory.h>  
        // #include <tchar.h>  
        ```  
  
    6.  針對 Windows Forms 應用程式，在 Form1.cpp，標記為註解`#include`參考 windows.h 陳述式。 例如:   
  
        ```  
        // #include <windows.h>  
        ```  
  
2.  Stdafx.h 中加入下列程式碼：  
  
    ```  
    #ifndef __FLTUSED__  
    #define __FLTUSED__  
       extern "C" __declspec(selectany) int _fltused=1;  
    #endif  
    ```  
  
3.  移除所有的 unmanaged 的類型：  
  
    1.  只要可行，來取代未受管理的類型結構中的參考[系統](https://msdn.microsoft.com/en-us/library/system.appdomainmanager.appdomainmanager.aspx)命名空間。 下表列出常見的 managed 型別：  
  
        |結構|描述|  
        |---------------|-----------------|  
        |[布林值](https://msdn.microsoft.com/en-us/library/system.boolean\(v=vs.140\).aspx)|表示布林值。|  
        |[Byte](https://msdn.microsoft.com/en-us/library/system.byte\(v=vs.140\).aspx)|代表 8 位元不帶正負號的整數。|  
        |[Char](https://msdn.microsoft.com/en-us/library/system.char\(v=vs.140\).aspx)|代表 Unicode 字元。|  
        |[DateTime](https://msdn.microsoft.com/en-us/library/system.datetime.datetime.aspx)|表示時間的瞬間，通常以一天的日期和時間表示。|  
        |[Decimal](https://msdn.microsoft.com/en-us/library/system.decimal\(v=vs.140\).aspx)|代表十進位數值。|  
        |[Double](https://msdn.microsoft.com/en-us/library/system.double\(v=vs.140\).aspx)|表示雙精度浮點數。|  
        |[Guid](https://msdn.microsoft.com/en-us/library/system.guid\(v=vs.140\).aspx)|表示全域唯一識別項 (GUID)。|  
        |[Int16](https://msdn.microsoft.com/en-us/library/system.int16\(v=vs.140\).aspx)|表示 16 位元帶正負號的整數。|  
        |[Int32](https://msdn.microsoft.com/en-us/library/system.int32\(v=vs.140\).aspx)|表示 32 位元帶正負號的整數。|  
        |[Int64](https://msdn.microsoft.com/en-us/library/system.int64\(v=vs.140\).aspx)|表示 64 位元帶正負號的整數。|  
        |[IntPtr](https://msdn.microsoft.com/en-us/library/system.intptr\(v=vs.140\).aspx)|平台專用的類型，用以代表指標或控點。|  
        |[SByte](https://msdn.microsoft.com/en-us/library/system.byte.aspx)|代表 8 位元帶正負號的整數。|  
        |[Single](https://msdn.microsoft.com/en-us/library/system.single.aspx)|表示單精確度浮點數。|  
        |[TimeSpan](https://msdn.microsoft.com/en-us/library/system.timespan\(v=vs.140\).aspx)|表示時間間隔。|  
        |[UInt16](https://msdn.microsoft.com/en-us/library/system.uint16\(v=vs.140\).aspx)|表示 16 位元不帶正負號的整數 (Unsigned Integer)。|  
        |[UInt32](https://msdn.microsoft.com/en-us/library/system.uint32\(v=vs.140\).aspx)|表示 32 位元不帶正負號的整數 (Unsigned Integer)。|  
        |[UInt64](https://msdn.microsoft.com/en-us/library/system.uint64\(v=vs.140\).aspx)|表示 64 位元不帶正負號的整數 (Unsigned Integer)。|  
        |[UIntPtr](https://msdn.microsoft.com/en-us/library/system.uintptr\(v=vs.140\).aspx)|平台專用的類型，用以代表指標或控點。|  
        |[void](https://msdn.microsoft.com/en-us/library/system.void\(v=vs.140\).aspx)|表示方法不會傳回值。也就是方法具有 void 傳回型別。|