---
title: -GENPROFILE, -FASTGENPROFILE (Generate Profiling Instrumented Build) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GENPROFILE
- FASTGENPROFILE
- /GENPROFILE
- /FASTGENPROFILE
helpviewer_keywords:
- GENPROFILE
- FASTGENPROFILE
ms.assetid: deff5ce7-46f5-448a-b9cd-a7a83a6864c6
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 2feec11d595584d4bfdd658f6b56a8cb4885de56

---
# /GENPROFILE, /FASTGENPROFILE (Generate Profiling Instrumented Build)
Specifies generation of a .pgd file by the linker to support profile-guided optimization (PGO).  /GENPROFILE and /FASTGENPROFILE use different default parameters. Use /GENPROFILE to favor precision over speed and memory usage during profiling. Use /FASTGENPROFILE to favor smaller memory usage and speed over precision.  
  
## Syntax  
  
```  
/{GENPROFILE|FASTGENPROFILE}[:{COUNTER32|COUNTER64|EXACT|MEMMAX=#|MEMMIN=#|NOEXACT|NOPATH|NOTRACKEH|PATH|PGD=filename|TRACKEH}]   
```  
  
## Remarks  
 COUNTER32 &#124; COUNTER64  
 Use COUNTER32 to specify the use of 32-bit probe counters, and COUNTER64 to specify  64-bit probe counters. When you specify /GENPROFILE, the default is COUNTER64. When you specify /FASTGENPROFILE, the default is COUNTER32.  
  
 EXACT &#124; NOEXACT  
 Use EXACT to specify thread-safe interlocked increments for probes. NOEXACT specifies unprotected increment operations for probes. The default is NOEXACT.  
  
 MEMMAX=value, MEMMIN=value  
 Use MEMMAX and MEMMIN to specify the maximum and minimum reservation sizes for training data in memory. The value is the amount of memory to reserve in bytes.  By default, these values are determined by an internal heuristic.  
  
 PATH &#124; NOPATH  
 Use PATH to specify a separate set of PGO counters for each unique path to a function. Use NOPATH to specify only one set of counters for each function.   When you specify /GENPROFILE, the default is PATH. When you specify /FASTGENPROFILE, the default is NOPATH.  
  
 TRACKEH &#124; NOTRACKEH  
 Specifies whether to use extra counters to keep an accurate count when exceptions are thrown during training. Use TRACKEH to specify extra counters for an exact count. Use NOTRACKEH to specify single counters for code that does not use exception handling or that does not encounter exceptions in your training scenarios.  When you specify /GENPROFILE, the default is TRACKEH. When you specify /FASTGENPROFILE, the default is NOTRACKEH.  
  
 PGD=filename  
 Specifies a base file name for the .pgd file. By default, the linker uses the base executable image file name with a .pgd extension.  
  
 The /GENPROFILE and /FASTGENPROFILE options tell the linker to generate the profiling instrumentation file needed to support application training for profile-guided optimization (PGO). The profiling information generated by application training is used as input to perform targeted whole-program optimizations during builds.   You can set additional options to control various profiling features for performance during app training and builds. The default options specified by /GENPROFILE give most accurate results, especially for large, complex multi-threaded apps. The /FASTGENPROFILE option uses different defaults for a lower memory footprint and faster performance during training, at the expense of accuracy.  
  
 Profiling information is captured when you run the instrumented app after you build by using /GENPROFILE of /FASTGENPROFILE. This information is used by the linker when you specify the /USEPROFILE option. For more information on how to train your app and details on the collected data, see Profile Guided Optimization.  
  
 You must also specify /LTCG when you specify /GENPROFILE or /FASTGENPROFILE.  
  
## See Also  
 [Setting Linker Options](../../build/reference/setting-linker-options.md)   
 [Linker Options](../../build/reference/linker-options.md)   
 [/LTCG (Link-time Code Generation)](../../build/reference/ltcg-link-time-code-generation.md)


<!--HONumber=Jan17_HO2-->


