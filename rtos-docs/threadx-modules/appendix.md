---
title: 부록 - 포트 관련 예제
description: 이 문서는 ThreadX 모듈의 포트 관련 예제를 보여줍니다.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c2324a2057bf2ddb2d255b2ff611d34fc664560a
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/07/2021
ms.locfileid: "106549813"
---
# <a name="appendix---port-specific-examples"></a><span data-ttu-id="11426-103">부록 - 포트 관련 예제</span><span class="sxs-lookup"><span data-stu-id="11426-103">Appendix - Port-specific examples</span></span>

## <a name="arm11-processor"></a><span data-ttu-id="11426-104">ARM11 프로세서</span><span class="sxs-lookup"><span data-stu-id="11426-104">ARM11 processor</span></span>

### <a name="arm11-using-gcc"></a><span data-ttu-id="11426-105">GCC를 사용하는 ARM11</span><span class="sxs-lookup"><span data-stu-id="11426-105">ARM11 using GCC</span></span>

#### <a name="module-preamble-for-arm11-using-gcc"></a><span data-ttu-id="11426-106">GCC를 사용하는 ARM11의 모듈 머리말</span><span class="sxs-lookup"><span data-stu-id="11426-106">Module preamble for ARM11 using GCC</span></span>

```armasm
    .arm
    .section .preamble, "ax"

    /* Define the module preamble.  */

    .global _txm_module_preamble
_txm_module_preamble:
    .word       0x4D4F4455                                      @ Module ID
    .word       0x5                                             @ Module Major Version
    .word       0x6                                             @ Module Minor Version
    .word       32                                              @ Module Preamble Size in 32-bit words
    .word       0x12345678                                      @ Module ID (application defined)
    .word       0x02000000                                      @ Module Properties where:
                                                                @   Bits 31-24: Compiler ID
                                                                @           0 -> IAR
                                                                @           1 -> ARM
                                                                @           2 -> GNU
    .word       _txm_module_thread_shell_entry - . - 0          @ Module Shell Entry Point
    .word       demo_module_start - . - 0                       @ Module Start Thread Entry Point
    .word       0                                               @ Module Stop Thread Entry Point
    .word       1                                               @ Module Start/Stop Thread Priority
    .word       1024                                            @ Module Start/Stop Thread Stack Size
    .word       _txm_module_callback_request_thread_entry - . - 0   @ Module Callback Thread Entry
    .word       1                                               @ Module Callback Thread Priority
    .word       1024                                            @ Module Callback Thread Stack Size
    .word       __code_size__                                   @ Module Code Size
    .word       __data_size__                                   @ Module Data Size
    .word       0                                               @ Reserved 0
    .word       0                                               @ Reserved 1
    .word       0                                               @ Reserved 2
    .word       0                                               @ Reserved 3
    .word       0                                               @ Reserved 4
    .word       0                                               @ Reserved 5
    .word       0                                               @ Reserved 6
    .word       0                                               @ Reserved 7  
    .word       0                                               @ Reserved 8  
    .word       0                                               @ Reserved 9
    .word       0                                               @ Reserved 10
    .word       0                                               @ Reserved 11
    .word       0                                               @ Reserved 12
    .word       0                                               @ Reserved 13
    .word       0                                               @ Reserved 14
    .word       0                                               @ Reserved 15
```

#### <a name="module-properties-for-arm11-using-gcc"></a><span data-ttu-id="11426-107">GCC를 사용하는 ARM11의 모듈 속성</span><span class="sxs-lookup"><span data-stu-id="11426-107">Module properties for ARM11 using GCC</span></span>

| <span data-ttu-id="11426-108">bit</span><span class="sxs-lookup"><span data-stu-id="11426-108">Bit</span></span> | <span data-ttu-id="11426-109">값</span><span class="sxs-lookup"><span data-stu-id="11426-109">Value</span></span> | <span data-ttu-id="11426-110">의미</span><span class="sxs-lookup"><span data-stu-id="11426-110">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="11426-111">[23-0]</span><span class="sxs-lookup"><span data-stu-id="11426-111">[23-0]</span></span> | <span data-ttu-id="11426-112">0</span><span class="sxs-lookup"><span data-stu-id="11426-112">0</span></span> | <span data-ttu-id="11426-113">예약됨</span><span class="sxs-lookup"><span data-stu-id="11426-113">Reserved</span></span>
| <span data-ttu-id="11426-114">[31-24]</span><span class="sxs-lookup"><span data-stu-id="11426-114">[31-24]</span></span> | <br /><span data-ttu-id="11426-115">0x00</span><span class="sxs-lookup"><span data-stu-id="11426-115">0x00</span></span><br /><span data-ttu-id="11426-116">0x01</span><span class="sxs-lookup"><span data-stu-id="11426-116">0x01</span></span><br /><span data-ttu-id="11426-117">0x02</span><span class="sxs-lookup"><span data-stu-id="11426-117">0x02</span></span> | <span data-ttu-id="11426-118">**컴파일러 ID**</span><span class="sxs-lookup"><span data-stu-id="11426-118">**Compiler ID**</span></span><br /><span data-ttu-id="11426-119">IAR</span><span class="sxs-lookup"><span data-stu-id="11426-119">IAR</span></span><br /><span data-ttu-id="11426-120">ARM</span><span class="sxs-lookup"><span data-stu-id="11426-120">ARM</span></span><br /><span data-ttu-id="11426-121">GNU</span><span class="sxs-lookup"><span data-stu-id="11426-121">GNU</span></span> |

#### <a name="module-linker-for-arm11-using-gcc"></a><span data-ttu-id="11426-122">GCC를 사용하는 ARM11의 모듈 링커</span><span class="sxs-lookup"><span data-stu-id="11426-122">Module linker for ARM11 using GCC</span></span>

```c
MEMORY
{
  FLASH (rx) : ORIGIN = 0x080F0000, LENGTH = 0x00010000
  RAM   (wx) : ORIGIN = 0x64001800, LENGTH = 0x00100000
}


SECTIONS
{
  __FLASH_segment_start__ = 0x080F0000;
  __FLASH_segment_end__   = 0x080FFFFF;
  __RAM_segment_start__   = 0x64001800;
  __RAM_segment_end__     = 0x64011800;

  __HEAPSIZE__ = 128;

  __preamble_load_start__ = __FLASH_segment_start__;
  .preamble __FLASH_segment_start__ : AT(__FLASH_segment_start__)
  {
    __preamble_start__ = .;
    *(.preamble .preamble.*)
  }
  __preamble_end__ = __preamble_start__ + SIZEOF(.preamble);

  __dynsym_load_start__ =  ALIGN(__preamble_end__ , 4);
  .dynsym ALIGN(__dynsym_load_start__ , 4) : AT(ALIGN(__dynsym_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynsym))
    KEEP (*(.dynsym*))
    . = ALIGN(4);
  }
  __dynsym_end__ = __dynsym_load_start__ + SIZEOF(.dynsym);

  __dynstr_load_start__ =  ALIGN(__dynsym_end__ , 4);
  .dynstr ALIGN(__dynstr_load_start__ , 4) : AT(ALIGN(__dynstr_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynstr))
    KEEP (*(.dynstr*))
    . = ALIGN(4);
  }
  __dynstr_end__ = __dynstr_load_start__ + SIZEOF(.dynstr);

  __reldyn_load_start__ =  ALIGN(__dynstr_end__ , 4);
  .rel.dyn ALIGN(__reldyn_load_start__ , 4) : AT(ALIGN(__reldyn_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.dyn))
    KEEP (*(.rel.dyn*))
    . = ALIGN(4);
  }
  __reldyn_end__ = __reldyn_load_start__ + SIZEOF(.rel.dyn);

  __relplt_load_start__ =  ALIGN(__reldyn_end__ , 4);
  .rel.plt ALIGN(__relplt_load_start__ , 4) : AT(ALIGN(__relplt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.plt))
    KEEP (*(.rel.plt*))
    . = ALIGN(4);
  }
  __relplt_end__ = __relplt_load_start__ + SIZEOF(.rel.plt);

  __plt_load_start__ =  ALIGN(__relplt_end__ , 4);
  .plt ALIGN(__plt_load_start__ , 4) : AT(ALIGN(__plt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.plt))
    KEEP (*(.plt*))
    . = ALIGN(4);
  }
  __plt_end__ = __plt_load_start__ + SIZEOF(.plt);

  __interp_load_start__ =  ALIGN(__plt_end__ , 4);
  .interp ALIGN(__interp_load_start__ , 4) : AT(ALIGN(__interp_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.interp))
    KEEP (*(.interp*))
    . = ALIGN(4);
  }
  __interp_end__ = __interp_load_start__ + SIZEOF(.interp);

  __hash_load_start__ =  ALIGN(__interp_end__ , 4);
  .hash ALIGN(__hash_load_start__ , 4) : AT(ALIGN(__hash_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.hash))
    KEEP (*(.hash*))
    . = ALIGN(4);
  }
  __hash_end__ = __hash_load_start__ + SIZEOF(.hash);

  __text_load_start__ =  ALIGN(__hash_end__ , 4);
  .text ALIGN(__text_load_start__ , 4) : AT(ALIGN(__text_load_start__, 4))
  {
    __text_start__ = .;
    *(.text .text.* .glue_7t .glue_7 .gnu.linkonce.t.* .gcc_except_table  )
  }
  __text_end__ = __text_start__ + SIZEOF(.text);

  __dtors_load_start__ = ALIGN(__text_end__ , 4);
  .dtors ALIGN(__text_end__ , 4) : AT(ALIGN(__text_end__ , 4))
  {
    __dtors_start__ = .;
    KEEP (*(SORT(.dtors.*))) KEEP (*(.dtors))
  }
  __dtors_end__ = __dtors_start__ + SIZEOF(.dtors);

  __ctors_load_start__ = ALIGN(__dtors_end__ , 4);
  .ctors ALIGN(__dtors_end__ , 4) : AT(ALIGN(__dtors_end__ , 4))
  {
    __ctors_start__ = .;
    KEEP (*(SORT(.ctors.*))) KEEP (*(.ctors))
  }
  __ctors_end__ = __ctors_start__ + SIZEOF(.ctors);

  __got_load_start__ = ALIGN(__ctors_end__ , 4);
  .got ALIGN(__ctors_end__ , 4) : AT(ALIGN(__ctors_end__ , 4))
  {
    . = ALIGN(4);
    _sgot = .;
    KEEP (*(.got))
    KEEP (*(.got*))
    . = ALIGN(4);
    _egot = .;
  }
  __got_end__ =  __got_load_start__ + SIZEOF(.got);

  __rodata_load_start__ = ALIGN(__got_end__ , 4);
  .rodata ALIGN(__got_end__ , 4) : AT(ALIGN(__got_end__ , 4))
  {
    __rodata_start__ = .;
    *(.rodata .rodata.* .gnu.linkonce.r.*)
  }
  __rodata_end__ = __rodata_start__ + SIZEOF(.rodata);

  __code_size__ =  __rodata_end__ - __FLASH_segment_start__;

  __fast_load_start__ = ALIGN(__rodata_end__ , 4);

  __fast_load_end__ = __fast_load_start__ + SIZEOF(.fast);

  __new_got_start__ = ALIGN(__RAM_segment_start__ , 4);

  __new_got_end__ =  __new_got_start__ + SIZEOF(.got);

  .fast ALIGN(__new_got_end__ , 4) : AT(ALIGN(__rodata_end__ , 4))
  {
    __fast_start__ = .;
    *(.fast .fast.*)
  }
  __fast_end__ = __fast_start__ + SIZEOF(.fast);

  .fast_run ALIGN(__fast_end__ , 4) (NOLOAD) :
  {
    __fast_run_start__ = .;
    . = MAX(__fast_run_start__ + SIZEOF(.fast), .);
  }
  __fast_run_end__ = __fast_run_start__ + SIZEOF(.fast_run);

  __data_load_start__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4);
  .data ALIGN(__fast_run_end__ , 4) : AT(ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4))
  {
    __data_start__ = .;
    *(.data .data.* .gnu.linkonce.d.*)
  }
  __data_end__ = __data_start__ + SIZEOF(.data);

  __data_load_end__ = __data_load_start__ + SIZEOF(.data);

  __FLASH_segment_used_end__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4) + SIZEOF(.data);

  .data_run ALIGN(__fast_run_end__ , 4) (NOLOAD) :
  {
    __data_run_start__ = .;
    . = MAX(__data_run_start__ + SIZEOF(.data), .);
  }
  __data_run_end__ = __data_run_start__ + SIZEOF(.data_run);

  __bss_load_start__ = ALIGN(__data_run_end__ , 4);
  .bss ALIGN(__data_run_end__ , 4) (NOLOAD) : AT(ALIGN(__data_run_end__ , 4))
  {
    __bss_start__ = .;
    *(.bss .bss.* .gnu.linkonce.b.*) *(COMMON)
  }
  __bss_end__ = __bss_start__ + SIZEOF(.bss);

  __non_init_load_start__ = ALIGN(__bss_end__ , 4);
  .non_init ALIGN(__bss_end__ , 4) (NOLOAD) : AT(ALIGN(__bss_end__ , 4))
  {
    __non_init_start__ = .;
    *(.non_init .non_init.*)
  }
  __non_init_end__ = __non_init_start__ + SIZEOF(.non_init);

  __heap_load_start__ = ALIGN(__non_init_end__ , 4);
  .heap ALIGN(__non_init_end__ , 4) (NOLOAD) : AT(ALIGN(__non_init_end__ , 4))
  {
    __heap_start__ = .;
    *(.heap)
    . = ALIGN(MAX(__heap_start__ + __HEAPSIZE__ , .), 4);
  }
  __heap_end__ = __heap_start__ + SIZEOF(.heap);

  __data_size__ =  __heap_end__ - __RAM_segment_start__;

}
```

#### <a name="building-modules-for-arm11-using-gcc"></a><span data-ttu-id="11426-123">GCC를 사용하는 ARM11의 모듈 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-123">Building Modules for ARM11 using GCC</span></span>

<span data-ttu-id="11426-124">GCC를 사용하여 ARM11 모듈을 빌드하는 간단한 명령줄 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-124">A simple command-line example for building an ARM11 module using GCC:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=arm1136j-s -msingle-pic-base -fPIC -mpic-register=r9 txm_module_preamble.S
arm-none-eabi-gcc -c -g -mcpu=arm1136j-s -msingle-pic-base -fPIC -mpic-register=r9 gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=arm1136j-s -msingle-pic-base -fPIC -mpic-register=r9 demo_threadx_module.c
arm-none-eabi-ld -A arm1136j-s -T demo_threadx_module.ld txm_module_preamble.o gcc_setup.o demo_threadx_module.o txm.a txm.a -o demo_threadx_module.out -M > demo_threadx_module.map
```

#### <a name="thread-extension-definition-for-arm11-using-gcc"></a><span data-ttu-id="11426-125">GCC를 사용하는 ARM11의 스레드 확장 정의</span><span class="sxs-lookup"><span data-stu-id="11426-125">Thread extension definition for ARM11 using GCC</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;  \
                                VOID    *tx_thread_module_entry_info_ptr;
```

#### <a name="building-module-manager-for-arm11-using-gcc"></a><span data-ttu-id="11426-126">GCC를 사용하는 ARM11의 모듈 관리자 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-126">Building Module Manager for ARM11 using GCC</span></span>

<span data-ttu-id="11426-127">예제는 제공되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-127">No example is provided.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-arm11-using-gcc"></a><span data-ttu-id="11426-128">GCC를 사용하는 ARM11의 외부 메모리 사용 API에 대한 특성</span><span class="sxs-lookup"><span data-stu-id="11426-128">Attributes for external memory enable API for ARM11 using GCC</span></span>

<span data-ttu-id="11426-129">이 기능은 이 포트에서 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-129">This feature not enabled on this port.</span></span>

### <a name="arm11-using-ac5"></a><span data-ttu-id="11426-130">AC5를 사용하는 ARM11</span><span class="sxs-lookup"><span data-stu-id="11426-130">ARM11 using AC5</span></span>

#### <a name="module-preamble-for-arm11-using-ac5"></a><span data-ttu-id="11426-131">AC5를 사용하는 ARM11의 모듈 머리말</span><span class="sxs-lookup"><span data-stu-id="11426-131">Module preamble for ARM11 using AC5</span></span>

```armasm
    AREA  Init, CODE, READONLY

;    /* Define public symbols.  */

    EXPORT __txm_module_preamble

;    /* Define application-specific start/stop entry points for the module.  */

    IMPORT demo_module_start

;    /* Define common external references.  */

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|

__txm_module_preamble
        DCD       0x4D4F4455                                        ; Module ID
        DCD       0x5                                               ; Module Major Version
        DCD       0x3                                               ; Module Minor Version
        DCD       32                                                ; Module Preamble Size in 32-bit words
        DCD       0x12345678                                        ; Module ID (application defined)
        DCD       0x01000000                                        ; Module Properties where:
                                                                    ;   Bits 31-24: Compiler ID
                                                                    ;           0 -> IAR
                                                                    ;           1 -> ARM
                                                                    ;           2 -> GNU
                                                                    ;   Bits 23-0:  Reserved
        DCD       _txm_module_thread_shell_entry - . + .            ; Module Shell Entry Point
        DCD       demo_module_start - . + .                         ; Module Start Thread Entry Point
        DCD       0                                                 ; Module Stop Thread Entry Point
        DCD       1                                                 ; Module Start/Stop Thread Priority
        DCD       1024                                              ; Module Start/Stop Thread Stack Size
        DCD       _txm_module_callback_request_thread_entry - . + . ; Module Callback Thread Entry
        DCD       1                                                 ; Module Callback Thread Priority
        DCD       1024                                              ; Module Callback Thread Stack Size
        DCD       |Image$$ER_RO$$Length|                            ; Module Code Size
        DCD       0x4000                                            ; Module Data Size - default to 16K (need to make sure this is large enough for module's data needs!)
        DCD       0                                                 ; Reserved 0
        DCD       0                                                 ; Reserved 1
        DCD       0                                                 ; Reserved 2
        DCD       0                                                 ; Reserved 3
        DCD       0                                                 ; Reserved 4
        DCD       0                                                 ; Reserved 5
        DCD       0                                                 ; Reserved 6
        DCD       0                                                 ; Reserved 7
        DCD       0                                                 ; Reserved 8  
        DCD       0                                                 ; Reserved 9
        DCD       0                                                 ; Reserved 10
        DCD       0                                                 ; Reserved 11
        DCD       0                                                 ; Reserved 12
        DCD       0                                                 ; Reserved 13
        DCD       0                                                 ; Reserved 14
        DCD       0                                                 ; Reserved 15

        END
```

#### <a name="module-properties-for-arm11-using-ac5"></a><span data-ttu-id="11426-132">AC5를 사용하는 ARM11의 모듈 속성</span><span class="sxs-lookup"><span data-stu-id="11426-132">Module properties for ARM11 using AC5</span></span>

| <span data-ttu-id="11426-133">bit</span><span class="sxs-lookup"><span data-stu-id="11426-133">Bit</span></span> | <span data-ttu-id="11426-134">값</span><span class="sxs-lookup"><span data-stu-id="11426-134">Value</span></span> | <span data-ttu-id="11426-135">의미</span><span class="sxs-lookup"><span data-stu-id="11426-135">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="11426-136">[23-0]</span><span class="sxs-lookup"><span data-stu-id="11426-136">[23-0]</span></span> | <span data-ttu-id="11426-137">0</span><span class="sxs-lookup"><span data-stu-id="11426-137">0</span></span> | <span data-ttu-id="11426-138">예약됨</span><span class="sxs-lookup"><span data-stu-id="11426-138">Reserved</span></span>
| <span data-ttu-id="11426-139">[31-24]</span><span class="sxs-lookup"><span data-stu-id="11426-139">[31-24]</span></span> | <br /><span data-ttu-id="11426-140">0x00</span><span class="sxs-lookup"><span data-stu-id="11426-140">0x00</span></span><br /><span data-ttu-id="11426-141">0x01</span><span class="sxs-lookup"><span data-stu-id="11426-141">0x01</span></span><br /><span data-ttu-id="11426-142">0x02</span><span class="sxs-lookup"><span data-stu-id="11426-142">0x02</span></span> | <span data-ttu-id="11426-143">**컴파일러 ID**</span><span class="sxs-lookup"><span data-stu-id="11426-143">**Compiler ID**</span></span><br /><span data-ttu-id="11426-144">IAR</span><span class="sxs-lookup"><span data-stu-id="11426-144">IAR</span></span><br /><span data-ttu-id="11426-145">ARM</span><span class="sxs-lookup"><span data-stu-id="11426-145">ARM</span></span><br /><span data-ttu-id="11426-146">GNU</span><span class="sxs-lookup"><span data-stu-id="11426-146">GNU</span></span> |

#### <a name="module-linker-for-arm11-using-ac5"></a><span data-ttu-id="11426-147">AC5를 사용하는 ARM11의 모듈 링커</span><span class="sxs-lookup"><span data-stu-id="11426-147">Module linker for ARM11 using AC5</span></span>

<span data-ttu-id="11426-148">명령줄을 기반으로 하며 링커 파일 예제는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-148">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-arm11-using-ac5"></a><span data-ttu-id="11426-149">AC5를 사용하는 ARM11의 모듈 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-149">Building Modules for ARM11 using AC5</span></span>

<span data-ttu-id="11426-150">AC5를 사용하여 ARM11 모듈을 빌드하는 간단한 명령줄 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-150">A simple command-line example for building an ARM11 module using AC5:</span></span>

```dos
armasm -g --cpu ARM1136J-S --apcs /interwork --apcs /ropi --apcs /rwpi txm_module_preamble.s
armcc -g -c -O0 --cpu ARM1136J-S --apcs /interwork --apcs /ropi --apcs /rwpi demo_threadx_module.c
armlink -d -o demo_threadx_module.axf --elf --ro 0 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list demo_threadx_module.map txm_module_preamble.o demo_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-arm11-using-ac5"></a><span data-ttu-id="11426-151">AC5를 사용하는 ARM11의 스레드 확장 정의</span><span class="sxs-lookup"><span data-stu-id="11426-151">Thread extension definition for ARM11 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;  \
                                VOID    *tx_thread_module_entry_info_ptr;
```

#### <a name="building-module-manager-for-arm11-using-ac5"></a><span data-ttu-id="11426-152">AC5를 사용하는 ARM11의 모듈 관리자 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-152">Building Module Manager for ARM11 using AC5</span></span>

<span data-ttu-id="11426-153">AC5를 사용하여 ARM11 모듈 관리자를 빌드하는 간단한 명령줄 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-153">A simple command-line example for building an ARM11 module manager using AC5:</span></span>

```dos
armasm -g --cpu ARM1136J-S --apcs /interwork tx_initialize_low_level.s
armcc -g -c -O2 --cpu ARM1136J-S --apcs /interwork demo_threadx_module_manager.c
armcc -g -c -O2 --cpu ARM1136J-S --apcs /interwork module_code.c
armlink -d -o demo_threadx_module_manager.axf --elf --ro 0 --first tx_initialize_low_level.o(Init) --remove --map --symbols --list demo_threadx_module_manager.map tx_initialize_low_level.o demo_threadx_module_manager.o module_code.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-arm11-using-ac5"></a><span data-ttu-id="11426-154">AC5를 사용하는 ARM11의 외부 메모리 사용 API에 대한 특성</span><span class="sxs-lookup"><span data-stu-id="11426-154">Attributes for external memory enable API for ARM11 using AC5</span></span>

<span data-ttu-id="11426-155">이 기능은 이 포트에서 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-155">This feature not enabled on this port.</span></span>

## <a name="cortex-a7-processor"></a><span data-ttu-id="11426-156">Cortex-A7 프로세서</span><span class="sxs-lookup"><span data-stu-id="11426-156">Cortex-A7 processor</span></span>

### <a name="cortex-a7-using-ac5"></a><span data-ttu-id="11426-157">AC5를 사용하는 Cortex-A7</span><span class="sxs-lookup"><span data-stu-id="11426-157">Cortex-A7 using AC5</span></span>

#### <a name="module-preamble-for-cortex-a7-using-ac5"></a><span data-ttu-id="11426-158">AC5를 사용하는 Cortex-A7의 모듈 머리말</span><span class="sxs-lookup"><span data-stu-id="11426-158">Module preamble for Cortex-A7 using AC5</span></span>

```armasm
    AREA  Init, CODE, READONLY

;    /* Define public symbols.  */

    EXPORT __txm_module_preamble

;    /* Define application-specific start/stop entry points for the module.  */

    IMPORT demo_module_start

;    /* Define common external references.  */

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|
    IMPORT  |Image$$ER_RW$$Length|

__txm_module_preamble
    DCD       0x4D4F4455                                        ; Module ID
    DCD       0x5                                               ; Module Major Version
    DCD       0x3                                               ; Module Minor Version
    DCD       32                                                ; Module Preamble Size in 32-bit words
    DCD       0x12345678                                        ; Module ID (application defined)
    DCD       0x01000001                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-1:  Reserved
                                                                ;   Bit 0:  0 -> Privileged mode execution (no MMU protection)
                                                                ;           1 -> User mode execution (MMU protection)
    DCD       _txm_module_thread_shell_entry - . + .            ; Module Shell Entry Point
    DCD       demo_module_start - . + .                         ; Module Start Thread Entry Point
    DCD       0                                                 ; Module Stop Thread Entry Point
    DCD       1                                                 ; Module Start/Stop Thread Priority
    DCD       1024                                              ; Module Start/Stop Thread Stack Size
    DCD       _txm_module_callback_request_thread_entry - . + . ; Module Callback Thread Entry
    DCD       1                                                 ; Module Callback Thread Priority
    DCD       1024                                              ; Module Callback Thread Stack Size
    DCD       |Image$$ER_RO$$Length| + |Image$$ER_RW$$Length|   ; Module Code Size
    DCD       0x4000                                            ; Module Data Size - default to 16K (need to make sure this is large enough for module's data needs!)
    DCD       0                                                 ; Reserved 0
    DCD       0                                                 ; Reserved 1
    DCD       0                                                 ; Reserved 2
    DCD       0                                                 ; Reserved 3
    DCD       0                                                 ; Reserved 4
    DCD       0                                                 ; Reserved 5
    DCD       0                                                 ; Reserved 6
    DCD       0                                                 ; Reserved 7
    DCD       0                                                 ; Reserved 8
    DCD       0                                                 ; Reserved 9
    DCD       0                                                 ; Reserved 10
    DCD       0                                                 ; Reserved 11
    DCD       0                                                 ; Reserved 12
    DCD       0                                                 ; Reserved 13
    DCD       0                                                 ; Reserved 14
    DCD       0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-a7-using-ac5"></a><span data-ttu-id="11426-159">AC5를 사용하는 Cortex-A7의 모듈 속성</span><span class="sxs-lookup"><span data-stu-id="11426-159">Module properties for Cortex-A7 using AC5</span></span>

| <span data-ttu-id="11426-160">bit</span><span class="sxs-lookup"><span data-stu-id="11426-160">Bit</span></span> | <span data-ttu-id="11426-161">값</span><span class="sxs-lookup"><span data-stu-id="11426-161">Value</span></span> | <span data-ttu-id="11426-162">의미</span><span class="sxs-lookup"><span data-stu-id="11426-162">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="11426-163">0</span><span class="sxs-lookup"><span data-stu-id="11426-163">0</span></span> | <span data-ttu-id="11426-164">0</span><span class="sxs-lookup"><span data-stu-id="11426-164">0</span></span><br /><span data-ttu-id="11426-165">1</span><span class="sxs-lookup"><span data-stu-id="11426-165">1</span></span> | <span data-ttu-id="11426-166">권한 있는 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-166">Privileged mode execution</span></span><br /><span data-ttu-id="11426-167">사용자 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-167">User mode execution</span></span> |
| <span data-ttu-id="11426-168">[23-1]</span><span class="sxs-lookup"><span data-stu-id="11426-168">[23-1]</span></span> | <span data-ttu-id="11426-169">0</span><span class="sxs-lookup"><span data-stu-id="11426-169">0</span></span> | <span data-ttu-id="11426-170">예약됨</span><span class="sxs-lookup"><span data-stu-id="11426-170">Reserved</span></span>
| <span data-ttu-id="11426-171">[31-24]</span><span class="sxs-lookup"><span data-stu-id="11426-171">[31-24]</span></span> | <br /><span data-ttu-id="11426-172">0x00</span><span class="sxs-lookup"><span data-stu-id="11426-172">0x00</span></span><br /><span data-ttu-id="11426-173">0x01</span><span class="sxs-lookup"><span data-stu-id="11426-173">0x01</span></span><br /><span data-ttu-id="11426-174">0x02</span><span class="sxs-lookup"><span data-stu-id="11426-174">0x02</span></span> | <span data-ttu-id="11426-175">**컴파일러 ID**</span><span class="sxs-lookup"><span data-stu-id="11426-175">**Compiler ID**</span></span><br /><span data-ttu-id="11426-176">IAR</span><span class="sxs-lookup"><span data-stu-id="11426-176">IAR</span></span><br /><span data-ttu-id="11426-177">ARM</span><span class="sxs-lookup"><span data-stu-id="11426-177">ARM</span></span><br /><span data-ttu-id="11426-178">GNU</span><span class="sxs-lookup"><span data-stu-id="11426-178">GNU</span></span> |

#### <a name="module-linker-for-cortex-a7-using-ac5"></a><span data-ttu-id="11426-179">AC5를 사용하는 Cortex-A7의 모듈 링커</span><span class="sxs-lookup"><span data-stu-id="11426-179">Module linker for Cortex-A7 using AC5</span></span>

<span data-ttu-id="11426-180">명령줄을 기반으로 하며 링커 파일 예제는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-180">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-cortex-a7-using-ac5"></a><span data-ttu-id="11426-181">AC5를 사용하는 Cortex-A7의 모듈 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-181">Building Modules for Cortex-A7 using AC5</span></span>

<span data-ttu-id="11426-182">AC5를 사용하여 Cortex-A7 모듈을 빌드하는 간단한 명령줄 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-182">A simple command-line example for building a Cortex-A7 module using AC5:</span></span>

```dos
armasm -g --cpu=cortex-a7.no_neon --fpu=softvfp --apcs=/interwork/ropi/rwpi txm_module_preamble.s
armcc  -g --cpu=cortex-a7.no_neon --fpu=softvfp -c --apcs=/interwork/ropi/rwpi --lower_ropi demo_threadx_module.c
armlink -d -o demo_threadx_module.axf --elf --ro 0 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list demo_threadx_module.map txm_module_preamble.o demo_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-a7-using-ac5"></a><span data-ttu-id="11426-183">AC5를 사용하는 Cortex-A7의 스레드 확장 정의</span><span class="sxs-lookup"><span data-stu-id="11426-183">Thread extension definition for Cortex-A7 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2   ULONG   tx_thread_vfp_enable;                   \
                                VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-a7-using-ac5"></a><span data-ttu-id="11426-184">AC5를 사용하는 Cortex-A7의 모듈 관리자 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-184">Building Module Manager for Cortex-A7 using AC5</span></span>

<span data-ttu-id="11426-185">AC5를 사용하여 Cortex-A7 모듈 관리자를 빌드하는 간단한 명령줄 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-185">A simple command-line example for building a Cortex-A7 module manager using AC5:</span></span>

```dos
armasm -g --cpu=cortex-a7.no_neon --fpu=softvfp --apcs=interwork tx_initialize_low_level.s
armcc -g --cpu=cortex-a7.no_neon --fpu=softvfp -c demo_threadx_module_manager.c
armcc -g --cpu=cortex-a7.no_neon --fpu=softvfp -c module_code.c
armlink -d -o demo_threadx_module_manager.axf --elf --ro 0x80000000 --first tx_initialize_low_level.o(VECTORS) --remove --map --symbols --list demo_threadx_module_manager.map tx_initialize_low_level.o demo_threadx_module_manager.o module_code.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-a7-using-ac5"></a><span data-ttu-id="11426-186">AC5를 사용하는 Cortex-A7의 외부 메모리 사용 API에 대한 특성</span><span class="sxs-lookup"><span data-stu-id="11426-186">Attributes for external memory enable API for Cortex-A7 using AC5</span></span>

<span data-ttu-id="11426-187">다음 특성을 사용하여 공유 메모리 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-187">The following attributes can be used to set up shared memory settings:</span></span>

| <span data-ttu-id="11426-188">특성 매개 변수</span><span class="sxs-lookup"><span data-stu-id="11426-188">Attribute parameter</span></span> | <span data-ttu-id="11426-189">의미</span><span class="sxs-lookup"><span data-stu-id="11426-189">Meaning</span></span> |
|---|---|
| <span data-ttu-id="11426-190">TXM_MMU_ATTRIBUTE_XN</span><span class="sxs-lookup"><span data-stu-id="11426-190">TXM_MMU_ATTRIBUTE_XN</span></span> | <span data-ttu-id="11426-191">실행 안 함</span><span class="sxs-lookup"><span data-stu-id="11426-191">Execute Never</span></span> |
| <span data-ttu-id="11426-192">TXM_MMU_ATTRIBUTE_B</span><span class="sxs-lookup"><span data-stu-id="11426-192">TXM_MMU_ATTRIBUTE_B</span></span> | <span data-ttu-id="11426-193">B 설정</span><span class="sxs-lookup"><span data-stu-id="11426-193">B setting</span></span> |
| <span data-ttu-id="11426-194">TXM_MMU_ATTRIBUTE_C</span><span class="sxs-lookup"><span data-stu-id="11426-194">TXM_MMU_ATTRIBUTE_C</span></span> | <span data-ttu-id="11426-195">C 설정</span><span class="sxs-lookup"><span data-stu-id="11426-195">C setting</span></span> |
| <span data-ttu-id="11426-196">TXM_MMU_ATTRIBUTE_AP</span><span class="sxs-lookup"><span data-stu-id="11426-196">TXM_MMU_ATTRIBUTE_AP</span></span> | <span data-ttu-id="11426-197">AP 설정</span><span class="sxs-lookup"><span data-stu-id="11426-197">AP setting</span></span> |
| <span data-ttu-id="11426-198">TXM_MMU_ATTRIBUTE_TEX</span><span class="sxs-lookup"><span data-stu-id="11426-198">TXM_MMU_ATTRIBUTE_TEX</span></span> | <span data-ttu-id="11426-199">TEX 설정</span><span class="sxs-lookup"><span data-stu-id="11426-199">TEX setting</span></span> |

<span data-ttu-id="11426-200">이러한 설정을 구성하는 방법은 ARM 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="11426-200">See ARM documentation for how these settings are configured.</span></span>

## <a name="cortex-m3-processor"></a><span data-ttu-id="11426-201">Cortex-M3 프로세서</span><span class="sxs-lookup"><span data-stu-id="11426-201">Cortex-M3 processor</span></span>

### <a name="cortex-m3-using-ac5"></a><span data-ttu-id="11426-202">AC5를 사용하는 Cortex-M3</span><span class="sxs-lookup"><span data-stu-id="11426-202">Cortex-M3 using AC5</span></span>

#### <a name="module-preamble-for-cortex-m3-using-ac5"></a><span data-ttu-id="11426-203">AC5를 사용하는 Cortex-M3의 모듈 머리말</span><span class="sxs-lookup"><span data-stu-id="11426-203">Module preamble for Cortex-M3 using AC5</span></span>

```armasm
    AREA Init, CODE, READONLY

    PRESERVE8

    ; Define public symbols

    EXPORT __txm_module_preamble

    ; Define application-specific start/stop entry points for the module

    EXTERN demo_module_start

    ; Define common external references

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|
    IMPORT  |Image$$ER_RW$$Length|
    IMPORT  |Image$$ER_RW$$RW$$Length|
    IMPORT  |Image$$ER_RW$$ZI$$Length|
    IMPORT  |Image$$ER_ZI$$ZI$$Length|

__txm_module_preamble
    DCD     0x4D4F4455                                          ; Module ID
    DCD     0x6                                                 ; Module Major Version
    DCD     0x1                                                 ; Module Minor Version
    DCD     32                                                  ; Module Preamble Size in 32-bit words
    DCD     0x12345678                                          ; Module ID (application defined)
    DCD     0x01000007                                          ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected)
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
    DCD     _txm_module_thread_shell_entry - __txm_module_preamble              ; Module Shell Entry Point
    DCD     demo_module_start - __txm_module_preamble           ; Module Start Thread Entry Point
    DCD     0                                                   ; Module Stop Thread Entry Point
    DCD     1                                                   ; Module Start/Stop Thread Priority
    DCD     1024                                                ; Module Start/Stop Thread Stack Size
    DCD     _txm_module_callback_request_thread_entry - __txm_module_preamble   ; Module Callback Thread Entry
    DCD     1                                                   ; Module Callback Thread Priority
    DCD     1024                                                ; Module Callback Thread Stack Size
    DCD     |Image$$ER_RO$$Length| + |Image$$ER_RW$$Length|         ; Module Code Size
    DCD     |Image$$ER_RW$$Length| + |Image$$ER_ZI$$ZI$$Length| ; Module Data Size
    DCD     0                                                   ; Reserved 0
    DCD     0                                                   ; Reserved 1
    DCD     0                                                   ; Reserved 2
    DCD     0                                                   ; Reserved 3
    DCD     0                                                   ; Reserved 4
    DCD     0                                                   ; Reserved 5
    DCD     0                                                   ; Reserved 6
    DCD     0                                                   ; Reserved 7
    DCD     0                                                   ; Reserved 8
    DCD     0                                                   ; Reserved 9
    DCD     0                                                   ; Reserved 10
    DCD     0                                                   ; Reserved 11
    DCD     0                                                   ; Reserved 12
    DCD     0                                                   ; Reserved 13
    DCD     0                                                   ; Reserved 14
    DCD     0                                                   ; Reserved 15

    END

```

#### <a name="module-properties-for-cortex-m3-using-ac5"></a><span data-ttu-id="11426-204">AC5를 사용하는 Cortex-M3의 모듈 속성</span><span class="sxs-lookup"><span data-stu-id="11426-204">Module properties for Cortex-M3 using AC5</span></span>

| <span data-ttu-id="11426-205">bit</span><span class="sxs-lookup"><span data-stu-id="11426-205">Bit</span></span> | <span data-ttu-id="11426-206">값</span><span class="sxs-lookup"><span data-stu-id="11426-206">Value</span></span> | <span data-ttu-id="11426-207">의미</span><span class="sxs-lookup"><span data-stu-id="11426-207">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="11426-208">0</span><span class="sxs-lookup"><span data-stu-id="11426-208">0</span></span> | <span data-ttu-id="11426-209">0</span><span class="sxs-lookup"><span data-stu-id="11426-209">0</span></span><br /><span data-ttu-id="11426-210">1</span><span class="sxs-lookup"><span data-stu-id="11426-210">1</span></span> | <span data-ttu-id="11426-211">권한 있는 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-211">Privileged mode execution</span></span><br /><span data-ttu-id="11426-212">사용자 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-212">User mode execution</span></span> |
| <span data-ttu-id="11426-213">1</span><span class="sxs-lookup"><span data-stu-id="11426-213">1</span></span> | <span data-ttu-id="11426-214">0</span><span class="sxs-lookup"><span data-stu-id="11426-214">0</span></span><br /><span data-ttu-id="11426-215">1</span><span class="sxs-lookup"><span data-stu-id="11426-215">1</span></span> | <span data-ttu-id="11426-216">MPU 보호 없음</span><span class="sxs-lookup"><span data-stu-id="11426-216">No MPU protection</span></span><br /><span data-ttu-id="11426-217">MPU 보호(사용자 모드가 선택되어 있어야 함)</span><span class="sxs-lookup"><span data-stu-id="11426-217">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="11426-218">2</span><span class="sxs-lookup"><span data-stu-id="11426-218">2</span></span> | <span data-ttu-id="11426-219">0</span><span class="sxs-lookup"><span data-stu-id="11426-219">0</span></span><br /><span data-ttu-id="11426-220">1</span><span class="sxs-lookup"><span data-stu-id="11426-220">1</span></span> | <span data-ttu-id="11426-221">공유/외부 메모리 액세스 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="11426-221">Disable shared/external memory access</span></span><br /><span data-ttu-id="11426-222">공유/외부 메모리 액세스 사용</span><span class="sxs-lookup"><span data-stu-id="11426-222">Enable shared/external memory access</span></span> |
| <span data-ttu-id="11426-223">[23-3]</span><span class="sxs-lookup"><span data-stu-id="11426-223">[23-3]</span></span> | <span data-ttu-id="11426-224">0</span><span class="sxs-lookup"><span data-stu-id="11426-224">0</span></span> | <span data-ttu-id="11426-225">예약됨</span><span class="sxs-lookup"><span data-stu-id="11426-225">Reserved</span></span>
| <span data-ttu-id="11426-226">[31-24]</span><span class="sxs-lookup"><span data-stu-id="11426-226">[31-24]</span></span> | <br /><span data-ttu-id="11426-227">0x00</span><span class="sxs-lookup"><span data-stu-id="11426-227">0x00</span></span><br /><span data-ttu-id="11426-228">0x01</span><span class="sxs-lookup"><span data-stu-id="11426-228">0x01</span></span><br /><span data-ttu-id="11426-229">0x02</span><span class="sxs-lookup"><span data-stu-id="11426-229">0x02</span></span> | <span data-ttu-id="11426-230">**컴파일러 ID**</span><span class="sxs-lookup"><span data-stu-id="11426-230">**Compiler ID**</span></span><br /><span data-ttu-id="11426-231">IAR</span><span class="sxs-lookup"><span data-stu-id="11426-231">IAR</span></span><br /><span data-ttu-id="11426-232">ARM</span><span class="sxs-lookup"><span data-stu-id="11426-232">ARM</span></span><br /><span data-ttu-id="11426-233">GNU</span><span class="sxs-lookup"><span data-stu-id="11426-233">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-ac5"></a><span data-ttu-id="11426-234">AC5를 사용하는 Cortex-M3의 모듈 링커</span><span class="sxs-lookup"><span data-stu-id="11426-234">Module linker for Cortex-M3 using AC5</span></span>

<span data-ttu-id="11426-235">예제 링커 파일은 제공되지 않으며 명령줄에서 링크가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="11426-235">No example linker file is provided; linking is done on the command line.</span></span> <span data-ttu-id="11426-236">다음 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="11426-236">See next section.</span></span>

#### <a name="building-modules-for-cortex-m3-using-ac5"></a><span data-ttu-id="11426-237">AC5를 사용하는 Cortex-M3의 모듈 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-237">Building Modules for Cortex-M3 using AC5</span></span>

<span data-ttu-id="11426-238">다음 예제 스크립트가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="11426-238">An example build script is provided:</span></span>

```dos
armasm -g --cpu=cortex-m3 --apcs=/interwork/ropi/rwpi txm_module_preamble.S
armcc  -g --cpu=cortex-m3 -c --apcs=/interwork/ropi/rwpi --lower_ropi -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module.c
armlink -d -o sample_threadx_module.axf --elf --ro=0x30000 --rw=0x40000 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list sample_threadx_module.map txm_module_preamble.o sample_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-m3-using-ac5"></a><span data-ttu-id="11426-239">AC5를 사용하는 Cortex-M3의 스레드 확장 정의</span><span class="sxs-lookup"><span data-stu-id="11426-239">Thread extension definition for Cortex-M3 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m3-using-ac5"></a><span data-ttu-id="11426-240">AC5를 사용하는 Cortex-M3의 모듈 관리자 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-240">Building Module Manager for Cortex-M3 using AC5</span></span>

<span data-ttu-id="11426-241">build_threadx_module_manager_demo.bat 예제를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="11426-241">See example build_threadx_module_manager_demo.bat:</span></span>

```dos
armasm -g --cpu=cortex-m3 --apcs=interwork tx_initialize_low_level.S
armcc -g --cpu=cortex-m3 -c -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module_manager.c
armlink -d -o sample_threadx_module_manager.axf --elf --ro 0x00000000 --first tx_initialize_low_level.o(RESET) --remove --map --symbols --list sample_threadx_module_manager.map tx_initialize_low_level.o sample_threadx_module_manager.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-ac5"></a><span data-ttu-id="11426-242">AC5를 사용하는 Cortex-M3의 외부 메모리 사용 API에 대한 특성</span><span class="sxs-lookup"><span data-stu-id="11426-242">Attributes for external memory enable API for Cortex-M3 using AC5</span></span>

<span data-ttu-id="11426-243">모듈에는 항상 공유 메모리에 대한 읽기 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-243">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="11426-244">특성 매개 변수</span><span class="sxs-lookup"><span data-stu-id="11426-244">Attribute parameter</span></span> | <span data-ttu-id="11426-245">의미</span><span class="sxs-lookup"><span data-stu-id="11426-245">Meaning</span></span> |
|---|---|
| <span data-ttu-id="11426-246">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="11426-246">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="11426-247">쓰기 액세스</span><span class="sxs-lookup"><span data-stu-id="11426-247">Write access</span></span> |

### <a name="cortex-m3-using-ac6"></a><span data-ttu-id="11426-248">AC6을 사용하는 Cortex-M3</span><span class="sxs-lookup"><span data-stu-id="11426-248">Cortex-M3 using AC6</span></span>

#### <a name="module-preamble-for-cortex-m3-using-ac6"></a><span data-ttu-id="11426-249">AC6을 사용하는 Cortex-M3의 모듈 머리말</span><span class="sxs-lookup"><span data-stu-id="11426-249">Module preamble for Cortex-M3 using AC6</span></span>

```armasm
    .text
    .align 4
    .syntax unified
    .section Init
    
    // Define public symbols
    .global __txm_module_preamble

    // Define application-specific start/stop entry points for the module
    .global demo_module_start

    // Define common external references
    .global  _txm_module_thread_shell_entry
    .global  _txm_module_callback_request_thread_entry

    .eabi_attribute Tag_ABI_PCS_RO_data, 1
    .eabi_attribute Tag_ABI_PCS_R9_use,  1
    .eabi_attribute Tag_ABI_PCS_RW_data, 2

__txm_module_preamble:
    .dc.l   0x4D4F4455                                          // Module ID
    .dc.l   0x6                                                 // Module Major Version
    .dc.l   0x1                                                 // Module Minor Version
    .dc.l   32                                                  // Module Preamble Size in 32-bit words
    .dc.l   0x12345678                                          // Module ID (application defined)
    .dc.l   0x01000007                                          // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    .dc.l   _txm_module_thread_shell_entry - __txm_module_preamble // Module Shell Entry Point
    .dc.l   demo_module_start - __txm_module_preamble           // Module Start Thread Entry Point
    .dc.l   0                                                   // Module Stop Thread Entry Point
    .dc.l   1                                                   // Module Start/Stop Thread Priority
    .dc.l   1024                                                // Module Start/Stop Thread Stack Size
    .dc.l   _txm_module_callback_request_thread_entry - __txm_module_preamble // Module Callback Thread Entry
    .dc.l   1                                                   // Module Callback Thread Priority
    .dc.l   1024                                                // Module Callback Thread Stack Size
    .dc.l   0x10000                                             // Module Code Size
    .dc.l   0x10000                                             // Module Data Size
    .dc.l   0                                                   // Reserved 0
    .dc.l   0                                                   // Reserved 1
    .dc.l   0                                                   // Reserved 2
    .dc.l   0                                                   // Reserved 3
    .dc.l   0                                                   // Reserved 4
    .dc.l   0                                                   // Reserved 5
    .dc.l   0                                                   // Reserved 6
    .dc.l   0                                                   // Reserved 7
    .dc.l   0                                                   // Reserved 8
    .dc.l   0                                                   // Reserved 9
    .dc.l   0                                                   // Reserved 10
    .dc.l   0                                                   // Reserved 11
    .dc.l   0                                                   // Reserved 12
    .dc.l   0                                                   // Reserved 13
    .dc.l   0                                                   // Reserved 14
    .dc.l   0                                                   // Reserved 15
```

#### <a name="module-properties-for-cortex-m3-using-ac6"></a><span data-ttu-id="11426-250">AC6을 사용하는 Cortex-M3의 모듈 속성</span><span class="sxs-lookup"><span data-stu-id="11426-250">Module properties for Cortex-M3 using AC6</span></span>

| <span data-ttu-id="11426-251">bit</span><span class="sxs-lookup"><span data-stu-id="11426-251">Bit</span></span> | <span data-ttu-id="11426-252">값</span><span class="sxs-lookup"><span data-stu-id="11426-252">Value</span></span> | <span data-ttu-id="11426-253">의미</span><span class="sxs-lookup"><span data-stu-id="11426-253">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="11426-254">0</span><span class="sxs-lookup"><span data-stu-id="11426-254">0</span></span> | <span data-ttu-id="11426-255">0</span><span class="sxs-lookup"><span data-stu-id="11426-255">0</span></span><br /><span data-ttu-id="11426-256">1</span><span class="sxs-lookup"><span data-stu-id="11426-256">1</span></span> | <span data-ttu-id="11426-257">권한 있는 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-257">Privileged mode execution</span></span><br /><span data-ttu-id="11426-258">사용자 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-258">User mode execution</span></span> |
| <span data-ttu-id="11426-259">1</span><span class="sxs-lookup"><span data-stu-id="11426-259">1</span></span> | <span data-ttu-id="11426-260">0</span><span class="sxs-lookup"><span data-stu-id="11426-260">0</span></span><br /><span data-ttu-id="11426-261">1</span><span class="sxs-lookup"><span data-stu-id="11426-261">1</span></span> | <span data-ttu-id="11426-262">MPU 보호 없음</span><span class="sxs-lookup"><span data-stu-id="11426-262">No MPU protection</span></span><br /><span data-ttu-id="11426-263">MPU 보호(사용자 모드가 선택되어 있어야 함)</span><span class="sxs-lookup"><span data-stu-id="11426-263">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="11426-264">2</span><span class="sxs-lookup"><span data-stu-id="11426-264">2</span></span> | <span data-ttu-id="11426-265">0</span><span class="sxs-lookup"><span data-stu-id="11426-265">0</span></span><br /><span data-ttu-id="11426-266">1</span><span class="sxs-lookup"><span data-stu-id="11426-266">1</span></span> | <span data-ttu-id="11426-267">공유/외부 메모리 액세스 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="11426-267">Disable shared/external memory access</span></span><br /><span data-ttu-id="11426-268">공유/외부 메모리 액세스 사용</span><span class="sxs-lookup"><span data-stu-id="11426-268">Enable shared/external memory access</span></span> |
| <span data-ttu-id="11426-269">[23-3]</span><span class="sxs-lookup"><span data-stu-id="11426-269">[23-3]</span></span> | <span data-ttu-id="11426-270">0</span><span class="sxs-lookup"><span data-stu-id="11426-270">0</span></span> | <span data-ttu-id="11426-271">예약됨</span><span class="sxs-lookup"><span data-stu-id="11426-271">Reserved</span></span>
| <span data-ttu-id="11426-272">[31-24]</span><span class="sxs-lookup"><span data-stu-id="11426-272">[31-24]</span></span> | <br /><span data-ttu-id="11426-273">0x00</span><span class="sxs-lookup"><span data-stu-id="11426-273">0x00</span></span><br /><span data-ttu-id="11426-274">0x01</span><span class="sxs-lookup"><span data-stu-id="11426-274">0x01</span></span><br /><span data-ttu-id="11426-275">0x02</span><span class="sxs-lookup"><span data-stu-id="11426-275">0x02</span></span> | <span data-ttu-id="11426-276">**컴파일러 ID**</span><span class="sxs-lookup"><span data-stu-id="11426-276">**Compiler ID**</span></span><br /><span data-ttu-id="11426-277">IAR</span><span class="sxs-lookup"><span data-stu-id="11426-277">IAR</span></span><br /><span data-ttu-id="11426-278">ARM</span><span class="sxs-lookup"><span data-stu-id="11426-278">ARM</span></span><br /><span data-ttu-id="11426-279">GNU</span><span class="sxs-lookup"><span data-stu-id="11426-279">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-ac6"></a><span data-ttu-id="11426-280">AC6을 사용하는 Cortex-M3의 모듈 링커</span><span class="sxs-lookup"><span data-stu-id="11426-280">Module linker for Cortex-M3 using AC6</span></span>

<span data-ttu-id="11426-281">링커 파일이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-281">No linker file is used.</span></span> <span data-ttu-id="11426-282">프로젝트 설정을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="11426-282">See project settings.</span></span>

#### <a name="building-modules-for-cortex-m3-using-ac6"></a><span data-ttu-id="11426-283">AC6을 사용하는 Cortex-M3의 모듈 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-283">Building Modules for Cortex-M3 using AC6</span></span>

<span data-ttu-id="11426-284">예제 작업 영역이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="11426-284">An example workspace is provided.</span></span> <span data-ttu-id="11426-285">ThreadX 라이브러리, ThreadX 모듈 라이브러리, 샘플 모듈 프로젝트 및 샘플 모듈 관리자 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="11426-285">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m3-using-ac6"></a><span data-ttu-id="11426-286">AC6을 사용하는 Cortex-M3의 스레드 확장 정의</span><span class="sxs-lookup"><span data-stu-id="11426-286">Thread extension definition for Cortex-M3 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m3-using-ac6"></a><span data-ttu-id="11426-287">AC6을 사용하는 Cortex-M3의 모듈 관리자 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-287">Building Module Manager for Cortex-M3 using AC6</span></span>

<span data-ttu-id="11426-288">예제 작업 영역이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="11426-288">An example workspace is provided.</span></span> <span data-ttu-id="11426-289">ThreadX 라이브러리, ThreadX 모듈 라이브러리, 샘플 모듈 프로젝트 및 샘플 모듈 관리자 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="11426-289">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-ac6"></a><span data-ttu-id="11426-290">AC6을 사용하는 Cortex-M3의 외부 메모리 사용 API에 대한 특성</span><span class="sxs-lookup"><span data-stu-id="11426-290">Attributes for external memory enable API for Cortex-M3 using AC6</span></span>

<span data-ttu-id="11426-291">모듈에는 항상 공유 메모리에 대한 읽기 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-291">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="11426-292">특성 매개 변수</span><span class="sxs-lookup"><span data-stu-id="11426-292">Attribute parameter</span></span> | <span data-ttu-id="11426-293">의미</span><span class="sxs-lookup"><span data-stu-id="11426-293">Meaning</span></span> |
|---|---|
| <span data-ttu-id="11426-294">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="11426-294">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="11426-295">쓰기 액세스</span><span class="sxs-lookup"><span data-stu-id="11426-295">Write access</span></span> |

### <a name="cortex-m3-using-gnu"></a><span data-ttu-id="11426-296">GNU를 사용하는 Cortex-M3</span><span class="sxs-lookup"><span data-stu-id="11426-296">Cortex-M3 using GNU</span></span>

#### <a name="module-preamble-for-cortex-m3-using-gnu"></a><span data-ttu-id="11426-297">GNU를 사용하는 Cortex-M3의 모듈 머리말</span><span class="sxs-lookup"><span data-stu-id="11426-297">Module preamble for Cortex-M3 using GNU</span></span>

```armasm
    .text
    .align 4
    .syntax unified

    /* Define public symbols.  */
    .global __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    .global demo_module_start

    /* Define common external refrences.  */
    .global _txm_module_thread_shell_entry
    .global _txm_module_callback_request_thread_entry

__txm_module_preamble:
    .dc.l      0x4D4F4455                                       // Module ID
    .dc.l      0x6                                              // Module Major Version
    .dc.l      0x1                                              // Module Minor Version
    .dc.l      32                                               // Module Preamble Size in 32-bit words
    .dc.l      0x12345678                                       // Module ID (application defined)
    .dc.l      0x02000007                                       // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bits 23-3: Reserved
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
    .dc.l      _txm_module_thread_shell_entry - . - 0           // Module Shell Entry Point
    .dc.l      demo_module_start - . - 0                        // Module Start Thread Entry Point
    .dc.l      0                                                // Module Stop Thread Entry Point 
    .dc.l      1                                                // Module Start/Stop Thread Priority
    .dc.l      1024                                             // Module Start/Stop Thread Stack Size
    .dc.l      _txm_module_callback_request_thread_entry - . - 0 // Module Callback Thread Entry
    .dc.l      1                                                // Module Callback Thread Priority
    .dc.l      1024                                             // Module Callback Thread Stack Size
    .dc.l      __code_size__                                    // Module Code Size
    .dc.l      __data_size__                                    // Module Data Size
    .dc.l      0                                                // Reserved 0
    .dc.l      0                                                // Reserved 1
    .dc.l      0                                                // Reserved 2
    .dc.l      0                                                // Reserved 3
    .dc.l      0                                                // Reserved 4
    .dc.l      0                                                // Reserved 5
    .dc.l      0                                                // Reserved 6
    .dc.l      0                                                // Reserved 7
    .dc.l      0                                                // Reserved 8
    .dc.l      0                                                // Reserved 9
    .dc.l      0                                                // Reserved 10
    .dc.l      0                                                // Reserved 11
    .dc.l      0                                                // Reserved 12
    .dc.l      0                                                // Reserved 13
    .dc.l      0                                                // Reserved 14
    .dc.l      0                                                // Reserved 15

```

#### <a name="module-properties-for-cortex-m3-using-gnu"></a><span data-ttu-id="11426-298">GNU를 사용하는 Cortex-M3의 모듈 속성</span><span class="sxs-lookup"><span data-stu-id="11426-298">Module properties for Cortex-M3 using GNU</span></span>

| <span data-ttu-id="11426-299">bit</span><span class="sxs-lookup"><span data-stu-id="11426-299">Bit</span></span> | <span data-ttu-id="11426-300">값</span><span class="sxs-lookup"><span data-stu-id="11426-300">Value</span></span> | <span data-ttu-id="11426-301">의미</span><span class="sxs-lookup"><span data-stu-id="11426-301">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="11426-302">0</span><span class="sxs-lookup"><span data-stu-id="11426-302">0</span></span> | <span data-ttu-id="11426-303">0</span><span class="sxs-lookup"><span data-stu-id="11426-303">0</span></span><br /><span data-ttu-id="11426-304">1</span><span class="sxs-lookup"><span data-stu-id="11426-304">1</span></span> | <span data-ttu-id="11426-305">권한 있는 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-305">Privileged mode execution</span></span><br /><span data-ttu-id="11426-306">사용자 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-306">User mode execution</span></span> |
| <span data-ttu-id="11426-307">1</span><span class="sxs-lookup"><span data-stu-id="11426-307">1</span></span> | <span data-ttu-id="11426-308">0</span><span class="sxs-lookup"><span data-stu-id="11426-308">0</span></span><br /><span data-ttu-id="11426-309">1</span><span class="sxs-lookup"><span data-stu-id="11426-309">1</span></span> | <span data-ttu-id="11426-310">MPU 보호 없음</span><span class="sxs-lookup"><span data-stu-id="11426-310">No MPU protection</span></span><br /><span data-ttu-id="11426-311">MPU 보호(사용자 모드가 선택되어 있어야 함)</span><span class="sxs-lookup"><span data-stu-id="11426-311">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="11426-312">2</span><span class="sxs-lookup"><span data-stu-id="11426-312">2</span></span> | <span data-ttu-id="11426-313">0</span><span class="sxs-lookup"><span data-stu-id="11426-313">0</span></span><br /><span data-ttu-id="11426-314">1</span><span class="sxs-lookup"><span data-stu-id="11426-314">1</span></span> | <span data-ttu-id="11426-315">공유/외부 메모리 액세스 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="11426-315">Disable shared/external memory access</span></span><br /><span data-ttu-id="11426-316">공유/외부 메모리 액세스 사용</span><span class="sxs-lookup"><span data-stu-id="11426-316">Enable shared/external memory access</span></span> |
| <span data-ttu-id="11426-317">[23-3]</span><span class="sxs-lookup"><span data-stu-id="11426-317">[23-3]</span></span> | <span data-ttu-id="11426-318">0</span><span class="sxs-lookup"><span data-stu-id="11426-318">0</span></span> | <span data-ttu-id="11426-319">예약됨</span><span class="sxs-lookup"><span data-stu-id="11426-319">Reserved</span></span>
| <span data-ttu-id="11426-320">[31-24]</span><span class="sxs-lookup"><span data-stu-id="11426-320">[31-24]</span></span> | <br /><span data-ttu-id="11426-321">0x00</span><span class="sxs-lookup"><span data-stu-id="11426-321">0x00</span></span><br /><span data-ttu-id="11426-322">0x01</span><span class="sxs-lookup"><span data-stu-id="11426-322">0x01</span></span><br /><span data-ttu-id="11426-323">0x02</span><span class="sxs-lookup"><span data-stu-id="11426-323">0x02</span></span> | <span data-ttu-id="11426-324">**컴파일러 ID**</span><span class="sxs-lookup"><span data-stu-id="11426-324">**Compiler ID**</span></span><br /><span data-ttu-id="11426-325">IAR</span><span class="sxs-lookup"><span data-stu-id="11426-325">IAR</span></span><br /><span data-ttu-id="11426-326">ARM</span><span class="sxs-lookup"><span data-stu-id="11426-326">ARM</span></span><br /><span data-ttu-id="11426-327">GNU</span><span class="sxs-lookup"><span data-stu-id="11426-327">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-gnu"></a><span data-ttu-id="11426-328">GNU를 사용하는 Cortex-M3의 모듈 링커</span><span class="sxs-lookup"><span data-stu-id="11426-328">Module linker for Cortex-M3 using GNU</span></span>

```c
MEMORY
{
  FLASH (rx) : ORIGIN = 0x00030000, LENGTH = 0x00010000
  RAM   (wx) : ORIGIN = 0, LENGTH = 0x00100000
}


SECTIONS
{
  __FLASH_segment_start__ = 0x00030000;
  __FLASH_segment_end__   = 0x00040000;
  __RAM_segment_start__   = 0;
  __RAM_segment_end__     = 0x8000;

  __HEAPSIZE__ = 128;

  __preamble_load_start__ = __FLASH_segment_start__;
  .preamble __FLASH_segment_start__ : AT(__FLASH_segment_start__)
  {
    __preamble_start__ = .;
    *(.preamble .preamble.*)
  }
  __preamble_end__ = __preamble_start__ + SIZEOF(.preamble);

  __dynsym_load_start__ =  ALIGN(__preamble_end__ , 4);
  .dynsym ALIGN(__dynsym_load_start__ , 4) : AT(ALIGN(__dynsym_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynsym))
    KEEP (*(.dynsym*))
    . = ALIGN(4);
  }
  __dynsym_end__ = __dynsym_load_start__ + SIZEOF(.dynsym);

  __dynstr_load_start__ =  ALIGN(__dynsym_end__ , 4);
  .dynstr ALIGN(__dynstr_load_start__ , 4) : AT(ALIGN(__dynstr_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynstr))
    KEEP (*(.dynstr*))
    . = ALIGN(4);
  }
  __dynstr_end__ = __dynstr_load_start__ + SIZEOF(.dynstr);

  __reldyn_load_start__ =  ALIGN(__dynstr_end__ , 4);
  .rel.dyn ALIGN(__reldyn_load_start__ , 4) : AT(ALIGN(__reldyn_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.dyn))
    KEEP (*(.rel.dyn*))
    . = ALIGN(4);
  }
  __reldyn_end__ = __reldyn_load_start__ + SIZEOF(.rel.dyn);

  __relplt_load_start__ =  ALIGN(__reldyn_end__ , 4);
  .rel.plt ALIGN(__relplt_load_start__ , 4) : AT(ALIGN(__relplt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.plt))
    KEEP (*(.rel.plt*))
    . = ALIGN(4);
  }
  __relplt_end__ = __relplt_load_start__ + SIZEOF(.rel.plt);

  __plt_load_start__ =  ALIGN(__relplt_end__ , 4);
  .plt ALIGN(__plt_load_start__ , 4) : AT(ALIGN(__plt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.plt))
    KEEP (*(.plt*))
    . = ALIGN(4);
  }
  __plt_end__ = __plt_load_start__ + SIZEOF(.plt);

  __interp_load_start__ =  ALIGN(__plt_end__ , 4);
  .interp ALIGN(__interp_load_start__ , 4) : AT(ALIGN(__interp_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.interp))
    KEEP (*(.interp*))
    . = ALIGN(4);
  }
  __interp_end__ = __interp_load_start__ + SIZEOF(.interp);

  __hash_load_start__ =  ALIGN(__interp_end__ , 4);
  .hash ALIGN(__hash_load_start__ , 4) : AT(ALIGN(__hash_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.hash))
    KEEP (*(.hash*))
    . = ALIGN(4);
  }
  __hash_end__ = __hash_load_start__ + SIZEOF(.hash);

  __text_load_start__ =  ALIGN(__hash_end__ , 4);
  .text ALIGN(__text_load_start__ , 4) : AT(ALIGN(__text_load_start__, 4))
  {
    __text_start__ = .;
    *(.text .text.* .glue_7t .glue_7 .gnu.linkonce.t.* .gcc_except_table  )
  }
  __text_end__ = __text_start__ + SIZEOF(.text);

  __dtors_load_start__ = ALIGN(__text_end__ , 4);
  .dtors ALIGN(__text_end__ , 4) : AT(ALIGN(__text_end__ , 4))
  {
    __dtors_start__ = .;
    KEEP (*(SORT(.dtors.*))) KEEP (*(.dtors))
  }
  __dtors_end__ = __dtors_start__ + SIZEOF(.dtors);

  __ctors_load_start__ = ALIGN(__dtors_end__ , 4);
  .ctors ALIGN(__dtors_end__ , 4) : AT(ALIGN(__dtors_end__ , 4))
  {
    __ctors_start__ = .;
    KEEP (*(SORT(.ctors.*))) KEEP (*(.ctors))
  }
  __ctors_end__ = __ctors_start__ + SIZEOF(.ctors);

  __got_load_start__ = ALIGN(__ctors_end__ , 4);
  .got ALIGN(__ctors_end__ , 4) : AT(ALIGN(__ctors_end__ , 4))
  {
    . = ALIGN(4);
    _sgot = .;
    KEEP (*(.got))
    KEEP (*(.got*))
    . = ALIGN(4);
    _egot = .;
  } 
  __got_end__ =  __got_load_start__ + SIZEOF(.got);

  __rodata_load_start__ = ALIGN(__got_end__ , 4);
  .rodata ALIGN(__got_end__ , 4) : AT(ALIGN(__got_end__ , 4))
  {
    __rodata_start__ = .;
    *(.rodata .rodata.* .gnu.linkonce.r.*)
  }
  __rodata_end__ = __rodata_start__ + SIZEOF(.rodata);
 
  __code_size__ =  __rodata_end__ - __FLASH_segment_start__;

  __fast_load_start__ = ALIGN(__rodata_end__ , 4);

  __fast_load_end__ = __fast_load_start__ + SIZEOF(.fast);

  __new_got_start__ = ALIGN(__RAM_segment_start__ , 4);

  __new_got_end__ =  __new_got_start__ + SIZEOF(.got);

  .fast ALIGN(__new_got_end__ , 4) : AT(ALIGN(__rodata_end__ , 4))
  {
    __fast_start__ = .;
    *(.fast .fast.*)
  }
  __fast_end__ = __fast_start__ + SIZEOF(.fast);

  .fast_run ALIGN(__fast_end__ , 4) (NOLOAD) :
  {
    __fast_run_start__ = .;
    . = MAX(__fast_run_start__ + SIZEOF(.fast), .);
  }
  __fast_run_end__ = __fast_run_start__ + SIZEOF(.fast_run);

  __data_load_start__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4);
  .data ALIGN(__fast_run_end__ , 4) : AT(ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4))
  {
    __data_start__ = .;
    *(.data .data.* .gnu.linkonce.d.*)
  }
  __data_end__ = __data_start__ + SIZEOF(.data);

  __data_load_end__ = __data_load_start__ + SIZEOF(.data);

  __FLASH_segment_used_end__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4) + SIZEOF(.data);

  .data_run ALIGN(__fast_run_end__ , 4) (NOLOAD) :
  {
    __data_run_start__ = .;
    . = MAX(__data_run_start__ + SIZEOF(.data), .);
  }
  __data_run_end__ = __data_run_start__ + SIZEOF(.data_run);

  __bss_load_start__ = ALIGN(__data_run_end__ , 4);
  .bss ALIGN(__data_run_end__ , 4) (NOLOAD) : AT(ALIGN(__data_run_end__ , 4))
  {
    __bss_start__ = .;
    *(.bss .bss.* .gnu.linkonce.b.*) *(COMMON)
  }
  __bss_end__ = __bss_start__ + SIZEOF(.bss);

  __non_init_load_start__ = ALIGN(__bss_end__ , 4);
  .non_init ALIGN(__bss_end__ , 4) (NOLOAD) : AT(ALIGN(__bss_end__ , 4))
  {
    __non_init_start__ = .;
    *(.non_init .non_init.*)
  }
  __non_init_end__ = __non_init_start__ + SIZEOF(.non_init);

  __heap_load_start__ = ALIGN(__non_init_end__ , 4);
  .heap ALIGN(__non_init_end__ , 4) (NOLOAD) : AT(ALIGN(__non_init_end__ , 4))
  {
    __heap_start__ = .;
    *(.heap)
    . = ALIGN(MAX(__heap_start__ + __HEAPSIZE__ , .), 4);
  }
  __heap_end__ = __heap_start__ + SIZEOF(.heap);

  __data_size__ =  __heap_end__ - __RAM_segment_start__;

}
```

#### <a name="building-modules-for-cortex-m3-using-gnu"></a><span data-ttu-id="11426-329">GNU를 사용하는 Cortex-M3의 모듈 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-329">Building Modules for Cortex-M3 using GNU</span></span>

<span data-ttu-id="11426-330">build_threadx_module_sample.bat를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="11426-330">See build_threadx_module_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base txm_module_preamble.s
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module.c
arm-none-eabi-ld -A cortex-m3 -T sample_threadx_module.ld txm_module_preamble.o gcc_setup.o sample_threadx_module.o -e _txm_module_thread_shell_entry txm.a -o sample_threadx_module.axf -M > sample_threadx_module.map
```

#### <a name="thread-extension-definition-for-cortex-m3-using-gnu"></a><span data-ttu-id="11426-331">GNU를 사용하는 Cortex-M3의 스레드 확장 정의</span><span class="sxs-lookup"><span data-stu-id="11426-331">Thread extension definition for Cortex-M3 using GNU</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m3-using-gnu"></a><span data-ttu-id="11426-332">GNU를 사용하는 Cortex-M3의 모듈 관리자 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-332">Building Module Manager for Cortex-M3 using GNU</span></span>

<span data-ttu-id="11426-333">build_threadx_module_manager_sample.bat를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="11426-333">See build_threadx_module_manager_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -mthumb -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module_manager.c
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -mthumb tx_simulator_startup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -mthumb cortexm_crt0.S
arm-none-eabi-ld -A cortex-m3 -ereset_handler -T sample_threadx.ld tx_simulator_startup.o cortexm_crt0.o sample_threadx_module_manager.o tx.a  libc.a -o sample_threadx_module_manager.axf -M > sample_threadx_module_manager.map
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-gnu"></a><span data-ttu-id="11426-334">GNU를 사용하는 Cortex-M3의 외부 메모리 사용 API에 대한 특성</span><span class="sxs-lookup"><span data-stu-id="11426-334">Attributes for external memory enable API for Cortex-M3 using GNU</span></span>

<span data-ttu-id="11426-335">모듈에는 항상 공유 메모리에 대한 읽기 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-335">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="11426-336">특성 매개 변수</span><span class="sxs-lookup"><span data-stu-id="11426-336">Attribute parameter</span></span> | <span data-ttu-id="11426-337">의미</span><span class="sxs-lookup"><span data-stu-id="11426-337">Meaning</span></span> |
|---|---|
| <span data-ttu-id="11426-338">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="11426-338">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="11426-339">쓰기 액세스</span><span class="sxs-lookup"><span data-stu-id="11426-339">Write access</span></span> |

### <a name="cortex-m3-using-iar"></a><span data-ttu-id="11426-340">IAR을 사용하는 Cortex-M3</span><span class="sxs-lookup"><span data-stu-id="11426-340">Cortex-M3 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m3-using-iar"></a><span data-ttu-id="11426-341">IAR을 사용하는 Cortex-M3의 모듈 머리말</span><span class="sxs-lookup"><span data-stu-id="11426-341">Module preamble for Cortex-M3 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */

    PUBLIC __txm_module_preamble


    /* Define application-specific start/stop entry points for the module.  */

    EXTERN demo_module_start


    /* Define common external references.  */

    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        ; Module ID
    DC32      0x5                                               ; Module Major Version
    DC32      0x6                                               ; Module Minor Version
    DC32      32                                                ; Module Preamble Size in 32-bit words
    DC32      0x12345678                                        ; Module ID (application defined)
    DC32      0x00000007                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-3: Reserved
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution


    DC32      _txm_module_thread_shell_entry - . - 0            ; Module Shell Entry Point
    DC32      demo_module_start - . - 0                         ; Module Start Thread Entry Point
    DC32      0                                                 ; Module Stop Thread Entry Point
    DC32      1                                                 ; Module Start/Stop Thread Priority
    DC32      1024                                              ; Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 ; Module Callback Thread Entry
    DC32      1                                                 ; Module Callback Thread Priority
    DC32      1024                                              ; Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      ; Module Code Size
    DC32      RWPI$$Length                                      ; Module Data Size
    DC32      0                                                 ; Reserved 0
    DC32      0                                                 ; Reserved 1
    DC32      0                                                 ; Reserved 2
    DC32      0                                                 ; Reserved 3
    DC32      0                                                 ; Reserved 4
    DC32      0                                                 ; Reserved 5
    DC32      0                                                 ; Reserved 6
    DC32      0                                                 ; Reserved 7
    DC32      0                                                 ; Reserved 8  
    DC32      0                                                 ; Reserved 9
    DC32      0                                                 ; Reserved 10
    DC32      0                                                 ; Reserved 11
    DC32      0                                                 ; Reserved 12
    DC32      0                                                 ; Reserved 13
    DC32      0                                                 ; Reserved 14
    DC32      0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m3-using-iar"></a><span data-ttu-id="11426-342">IAR을 사용하는 Cortex-M3의 모듈 속성</span><span class="sxs-lookup"><span data-stu-id="11426-342">Module properties for Cortex-M3 using IAR</span></span>

| <span data-ttu-id="11426-343">bit</span><span class="sxs-lookup"><span data-stu-id="11426-343">Bit</span></span> | <span data-ttu-id="11426-344">값</span><span class="sxs-lookup"><span data-stu-id="11426-344">Value</span></span> | <span data-ttu-id="11426-345">의미</span><span class="sxs-lookup"><span data-stu-id="11426-345">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="11426-346">0</span><span class="sxs-lookup"><span data-stu-id="11426-346">0</span></span> | <span data-ttu-id="11426-347">0</span><span class="sxs-lookup"><span data-stu-id="11426-347">0</span></span><br /><span data-ttu-id="11426-348">1</span><span class="sxs-lookup"><span data-stu-id="11426-348">1</span></span> | <span data-ttu-id="11426-349">권한 있는 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-349">Privileged mode execution</span></span><br /><span data-ttu-id="11426-350">사용자 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-350">User mode execution</span></span> |
| <span data-ttu-id="11426-351">1</span><span class="sxs-lookup"><span data-stu-id="11426-351">1</span></span> | <span data-ttu-id="11426-352">0</span><span class="sxs-lookup"><span data-stu-id="11426-352">0</span></span><br /><span data-ttu-id="11426-353">1</span><span class="sxs-lookup"><span data-stu-id="11426-353">1</span></span> | <span data-ttu-id="11426-354">MPU 보호 없음</span><span class="sxs-lookup"><span data-stu-id="11426-354">No MPU protection</span></span><br /><span data-ttu-id="11426-355">MPU 보호(사용자 모드가 선택되어 있어야 함)</span><span class="sxs-lookup"><span data-stu-id="11426-355">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="11426-356">2</span><span class="sxs-lookup"><span data-stu-id="11426-356">2</span></span> | <span data-ttu-id="11426-357">0</span><span class="sxs-lookup"><span data-stu-id="11426-357">0</span></span><br /><span data-ttu-id="11426-358">1</span><span class="sxs-lookup"><span data-stu-id="11426-358">1</span></span> | <span data-ttu-id="11426-359">공유/외부 메모리 액세스 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="11426-359">Disable shared/external memory access</span></span><br /><span data-ttu-id="11426-360">공유/외부 메모리 액세스 사용</span><span class="sxs-lookup"><span data-stu-id="11426-360">Enable shared/external memory access</span></span> |
| <span data-ttu-id="11426-361">[23-3]</span><span class="sxs-lookup"><span data-stu-id="11426-361">[23-3]</span></span> | <span data-ttu-id="11426-362">0</span><span class="sxs-lookup"><span data-stu-id="11426-362">0</span></span> | <span data-ttu-id="11426-363">예약됨</span><span class="sxs-lookup"><span data-stu-id="11426-363">Reserved</span></span>
| <span data-ttu-id="11426-364">[31-24]</span><span class="sxs-lookup"><span data-stu-id="11426-364">[31-24]</span></span> | <br /><span data-ttu-id="11426-365">0x00</span><span class="sxs-lookup"><span data-stu-id="11426-365">0x00</span></span><br /><span data-ttu-id="11426-366">0x01</span><span class="sxs-lookup"><span data-stu-id="11426-366">0x01</span></span><br /><span data-ttu-id="11426-367">0x02</span><span class="sxs-lookup"><span data-stu-id="11426-367">0x02</span></span> | <span data-ttu-id="11426-368">**컴파일러 ID**</span><span class="sxs-lookup"><span data-stu-id="11426-368">**Compiler ID**</span></span><br /><span data-ttu-id="11426-369">IAR</span><span class="sxs-lookup"><span data-stu-id="11426-369">IAR</span></span><br /><span data-ttu-id="11426-370">ARM</span><span class="sxs-lookup"><span data-stu-id="11426-370">ARM</span></span><br /><span data-ttu-id="11426-371">GNU</span><span class="sxs-lookup"><span data-stu-id="11426-371">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-iar"></a><span data-ttu-id="11426-372">IAR을 사용하는 Cortex-M3의 모듈 링커</span><span class="sxs-lookup"><span data-stu-id="11426-372">Module linker for Cortex-M3 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\a_v1_0.xml" */
/*-Specials-*/
define symbol __ICFEDIT_intvec_start__ = 0x0;
/*-Memory Regions-*/
define symbol __ICFEDIT_region_ROM_start__ = 0x080f0000;
define symbol __ICFEDIT_region_ROM_end__   = 0x080fffff;
define symbol __ICFEDIT_region_RAM_start__ = 0x64002800;
define symbol __ICFEDIT_region_RAM_end__   = 0x64100000;
/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__   = 0;
define symbol __ICFEDIT_size_svcstack__ = 0;
define symbol __ICFEDIT_size_irqstack__ = 0;
define symbol __ICFEDIT_size_fiqstack__ = 0;
define symbol __ICFEDIT_size_undstack__ = 0;
define symbol __ICFEDIT_size_abtstack__ = 0;
define symbol __ICFEDIT_size_heap__     = 0x1000;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region ROM_region   = mem:[from __ICFEDIT_region_ROM_start__   to __ICFEDIT_region_ROM_end__];
define region RAM_region   = mem:[from __ICFEDIT_region_RAM_start__   to __ICFEDIT_region_RAM_end__];

//define block CSTACK    with alignment = 8, size = __ICFEDIT_size_cstack__   { };
//define block SVC_STACK with alignment = 8, size = __ICFEDIT_size_svcstack__ { };
//define block IRQ_STACK with alignment = 8, size = __ICFEDIT_size_irqstack__ { };
//define block FIQ_STACK with alignment = 8, size = __ICFEDIT_size_fiqstack__ { };
//define block UND_STACK with alignment = 8, size = __ICFEDIT_size_undstack__ { };
//define block ABT_STACK with alignment = 8, size = __ICFEDIT_size_abtstack__ { };
define block HEAP      with alignment = 8, size = __ICFEDIT_size_heap__     { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

//place at address mem:__ICFEDIT_intvec_start__ { readonly section .intvec };

define movable block ROPI with alignment = 4, fixed order
{
  ro object txm_module_preamble_stm32f2xx.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-m3-using-iar"></a><span data-ttu-id="11426-373">IAR을 사용하는 Cortex-M3의 모듈 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-373">Building Modules for Cortex-M3 using IAR</span></span>

<span data-ttu-id="11426-374">예제 작업 영역이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="11426-374">An example workspace is provided.</span></span> <span data-ttu-id="11426-375">ThreadX 라이브러리, ThreadX 모듈 라이브러리, 데모 모듈 프로젝트 및 데모 모듈 관리자 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="11426-375">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m3-using-iar"></a><span data-ttu-id="11426-376">IAR을 사용하는 Cortex-M3의 스레드 확장 정의</span><span class="sxs-lookup"><span data-stu-id="11426-376">Thread extension definition for Cortex-M3 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_saved_lr;              \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-m3-using-iar"></a><span data-ttu-id="11426-377">IAR을 사용하는 Cortex-M3의 모듈 관리자 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-377">Building Module Manager for Cortex-M3 using IAR</span></span>

<span data-ttu-id="11426-378">예제 작업 영역이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="11426-378">An example workspace is provided.</span></span> <span data-ttu-id="11426-379">ThreadX 라이브러리, ThreadX 모듈 라이브러리, 데모 모듈 프로젝트 및 데모 모듈 관리자 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="11426-379">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-iar"></a><span data-ttu-id="11426-380">IAR을 사용하는 Cortex-M3의 외부 메모리 사용 API에 대한 특성</span><span class="sxs-lookup"><span data-stu-id="11426-380">Attributes for external memory enable API for Cortex-M3 using IAR</span></span>

<span data-ttu-id="11426-381">모듈에는 항상 공유 메모리에 대한 읽기 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-381">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="11426-382">특성 매개 변수</span><span class="sxs-lookup"><span data-stu-id="11426-382">Attribute parameter</span></span> | <span data-ttu-id="11426-383">의미</span><span class="sxs-lookup"><span data-stu-id="11426-383">Meaning</span></span> |
|---|---|
| <span data-ttu-id="11426-384">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="11426-384">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="11426-385">쓰기 액세스</span><span class="sxs-lookup"><span data-stu-id="11426-385">Write access</span></span> |

## <a name="cortex-m33-processor"></a><span data-ttu-id="11426-386">Cortex-M33 프로세서</span><span class="sxs-lookup"><span data-stu-id="11426-386">Cortex-M33 processor</span></span>

### <a name="cortex-m33-using-ac6"></a><span data-ttu-id="11426-387">AC6을 사용하는 Cortex-M33</span><span class="sxs-lookup"><span data-stu-id="11426-387">Cortex-M33 using AC6</span></span>

#### <a name="module-preamble-for-cortex-m33-using-ac6"></a><span data-ttu-id="11426-388">AC6을 사용하는 Cortex-M33의 모듈 머리말</span><span class="sxs-lookup"><span data-stu-id="11426-388">Module preamble for Cortex-M33 using AC6</span></span>

```c
    .text
    .align 4
    .syntax unified
    .section RESET
    
    // Define public symbols
    .global __txm_module_preamble

    // Define application-specific start/stop entry points for the module
    .global demo_module_start

    // Define common external references
    .global  _txm_module_thread_shell_entry
    .global  _txm_module_callback_request_thread_entry

    .eabi_attribute Tag_ABI_PCS_RO_data, 1
    .eabi_attribute Tag_ABI_PCS_R9_use,  1
    .eabi_attribute Tag_ABI_PCS_RW_data, 2

__txm_module_preamble:
    .dc.l   0x4D4F4455                                          // Module ID
    .dc.l   0x6                                                 // Module Major Version
    .dc.l   0x1                                                 // Module Minor Version
    .dc.l   32                                                  // Module Preamble Size in 32-bit words
    .dc.l   0x12345678                                          // Module ID (application defined)
    .dc.l   0x01000007                                          // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    .dc.l   _txm_module_thread_shell_entry - __txm_module_preamble // Module Shell Entry Point
    .dc.l   demo_module_start - __txm_module_preamble           // Module Start Thread Entry Point
    .dc.l   0                                                   // Module Stop Thread Entry Point
    .dc.l   1                                                   // Module Start/Stop Thread Priority
    .dc.l   1024                                                // Module Start/Stop Thread Stack Size
    .dc.l   _txm_module_callback_request_thread_entry - __txm_module_preamble // Module Callback Thread Entry
    .dc.l   1                                                   // Module Callback Thread Priority
    .dc.l   1024                                                // Module Callback Thread Stack Size
    //the tools can't add two symbols together, but it should look like this:
    //.dc.l   Image$$ER_RO$$Length + Image$$ER_RW$$Length         // Module Code Size
    //.dc.l   Image$$ER_RW$$Length + Image$$ER_ZI$$ZI$$Length     // Module Data Size
    //so instead we'll define hard values:
    .dc.l   0x4000                                              // Module Code Size
    .dc.l   0x4000                                              // Module Data Size
    .dc.l   0                                                   // Reserved 0
    .dc.l   0                                                   // Reserved 1
    .dc.l   0                                                   // Reserved 2
    .dc.l   0                                                   // Reserved 3
    .dc.l   0                                                   // Reserved 4
    .dc.l   0                                                   // Reserved 5
    .dc.l   0                                                   // Reserved 6
    .dc.l   0                                                   // Reserved 7
    .dc.l   0                                                   // Reserved 8
    .dc.l   0                                                   // Reserved 9
    .dc.l   0                                                   // Reserved 10
    .dc.l   0                                                   // Reserved 11
    .dc.l   0                                                   // Reserved 12
    .dc.l   0                                                   // Reserved 13
    .dc.l   0                                                   // Reserved 14
    .dc.l   0                                                   // Reserved 15
```

#### <a name="module-properties-for-cortex-m33-using-ac6"></a><span data-ttu-id="11426-389">AC6을 사용하는 Cortex-M33의 모듈 속성</span><span class="sxs-lookup"><span data-stu-id="11426-389">Module properties for Cortex-M33 using AC6</span></span>

| <span data-ttu-id="11426-390">bit</span><span class="sxs-lookup"><span data-stu-id="11426-390">Bit</span></span> | <span data-ttu-id="11426-391">값</span><span class="sxs-lookup"><span data-stu-id="11426-391">Value</span></span> | <span data-ttu-id="11426-392">의미</span><span class="sxs-lookup"><span data-stu-id="11426-392">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="11426-393">0</span><span class="sxs-lookup"><span data-stu-id="11426-393">0</span></span> | <span data-ttu-id="11426-394">0</span><span class="sxs-lookup"><span data-stu-id="11426-394">0</span></span><br /><span data-ttu-id="11426-395">1</span><span class="sxs-lookup"><span data-stu-id="11426-395">1</span></span> | <span data-ttu-id="11426-396">권한 있는 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-396">Privileged mode execution</span></span><br /><span data-ttu-id="11426-397">사용자 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-397">User mode execution</span></span> |
| <span data-ttu-id="11426-398">1</span><span class="sxs-lookup"><span data-stu-id="11426-398">1</span></span> | <span data-ttu-id="11426-399">0</span><span class="sxs-lookup"><span data-stu-id="11426-399">0</span></span><br /><span data-ttu-id="11426-400">1</span><span class="sxs-lookup"><span data-stu-id="11426-400">1</span></span> | <span data-ttu-id="11426-401">MPU 보호 없음</span><span class="sxs-lookup"><span data-stu-id="11426-401">No MPU protection</span></span><br /><span data-ttu-id="11426-402">MPU 보호(사용자 모드가 선택되어 있어야 함)</span><span class="sxs-lookup"><span data-stu-id="11426-402">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="11426-403">2</span><span class="sxs-lookup"><span data-stu-id="11426-403">2</span></span> | <span data-ttu-id="11426-404">0</span><span class="sxs-lookup"><span data-stu-id="11426-404">0</span></span><br /><span data-ttu-id="11426-405">1</span><span class="sxs-lookup"><span data-stu-id="11426-405">1</span></span> | <span data-ttu-id="11426-406">공유/외부 메모리 액세스 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="11426-406">Disable shared/external memory access</span></span><br /><span data-ttu-id="11426-407">공유/외부 메모리 액세스 사용</span><span class="sxs-lookup"><span data-stu-id="11426-407">Enable shared/external memory access</span></span> |
| <span data-ttu-id="11426-408">[23-3]</span><span class="sxs-lookup"><span data-stu-id="11426-408">[23-3]</span></span> | <span data-ttu-id="11426-409">0</span><span class="sxs-lookup"><span data-stu-id="11426-409">0</span></span> | <span data-ttu-id="11426-410">예약됨</span><span class="sxs-lookup"><span data-stu-id="11426-410">Reserved</span></span>
| <span data-ttu-id="11426-411">[31-24]</span><span class="sxs-lookup"><span data-stu-id="11426-411">[31-24]</span></span> | <br /><span data-ttu-id="11426-412">0x00</span><span class="sxs-lookup"><span data-stu-id="11426-412">0x00</span></span><br /><span data-ttu-id="11426-413">0x01</span><span class="sxs-lookup"><span data-stu-id="11426-413">0x01</span></span><br /><span data-ttu-id="11426-414">0x02</span><span class="sxs-lookup"><span data-stu-id="11426-414">0x02</span></span> | <span data-ttu-id="11426-415">**컴파일러 ID**</span><span class="sxs-lookup"><span data-stu-id="11426-415">**Compiler ID**</span></span><br /><span data-ttu-id="11426-416">IAR</span><span class="sxs-lookup"><span data-stu-id="11426-416">IAR</span></span><br /><span data-ttu-id="11426-417">ARM</span><span class="sxs-lookup"><span data-stu-id="11426-417">ARM</span></span><br /><span data-ttu-id="11426-418">GNU</span><span class="sxs-lookup"><span data-stu-id="11426-418">GNU</span></span> |

#### <a name="module-linker-for-cortex-m33-using-ac6"></a><span data-ttu-id="11426-419">AC6을 사용하는 Cortex-M33의 모듈 링커</span><span class="sxs-lookup"><span data-stu-id="11426-419">Module linker for Cortex-M33 using AC6</span></span>

<span data-ttu-id="11426-420">Keil 도구 체인에는 링커 파일이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-420">No linker file needed for Keil toolchain.</span></span> <span data-ttu-id="11426-421">예제 프로젝트의 빌드 설정을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="11426-421">See build settings in example project.</span></span>
<span data-ttu-id="11426-422">중요한 링커 옵션은 아래와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-422">Important linker options are listed below:</span></span>

```c
--entry demo_module_start --first __txm_module_preamble
```

#### <a name="building-modules-for-cortex-m33-using-ac6"></a><span data-ttu-id="11426-423">AC6을 사용하는 Cortex-M33의 모듈 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-423">Building Modules for Cortex-M33 using AC6</span></span>

<span data-ttu-id="11426-424">컴파일러 설정:</span><span class="sxs-lookup"><span data-stu-id="11426-424">Compiler settings:</span></span>

```c
-xc -std=c99 --target=arm-arm-none-eabi -mcpu=cortex-m33 -mfpu=fpv5-sp-d16 -mfloat-abi=hard -c
-fno-rtti -funsigned-char -fshort-enums -fshort-wchar
-mlittle-endian -gdwarf-3 -fropi -frwpi -O1 -ffunction-sections -Wno-packed -Wno-missing-variable-declarations -Wno-missing-prototypes -Wno-missing-noreturn -Wno-sign-conversion -Wno-nonportable-include-path -Wno-reserved-id-macro -Wno-unused-macros -Wno-documentation-unknown-command -Wno-documentation -Wno-license-management -Wno-parentheses-equality -I ../../../../../common_modules/inc -I ../../../../../common/inc -I ../../../../../ports_module/cortex_m33/ac6/inc -I ../demo_secure_zone
-I./RTE/_FVP_Simulation_Model
-IC:/Users/your_path/AppData/Local/Arm/Packs/ARM/CMSIS/5.5.1/CMSIS/Core/Include
-IC:/Users/your_path/AppData/Local/Arm/Packs/ARM/CMSIS/5.5.1/Device/ARM/ARMCM33/Include
-D__UVISION_VERSION="531" -D_RTE_ -DARMCM33_DSP_FP_TZ -D_RTE_
-o ./Objects/*.o -MD
```

#### <a name="thread-extension-definition-for-cortex-m33-using-ac6"></a><span data-ttu-id="11426-425">AC6을 사용하는 Cortex-M33의 스레드 확장 정의</span><span class="sxs-lookup"><span data-stu-id="11426-425">Thread extension definition for Cortex-M33 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2                   VOID    *tx_thread_module_instance_ptr;         \
                                                VOID    *tx_thread_module_entry_info_ptr;       \
                                                ULONG   tx_thread_module_current_user_mode;     \
                                                ULONG   tx_thread_module_user_mode;             \
                                                ULONG   tx_thread_module_saved_lr;              \
                                                VOID    *tx_thread_module_kernel_stack_start;   \
                                                VOID    *tx_thread_module_kernel_stack_end;     \
                                                ULONG   tx_thread_module_kernel_stack_size;     \
                                                VOID    *tx_thread_module_stack_ptr;            \
                                                VOID    *tx_thread_module_stack_start;          \
                                                VOID    *tx_thread_module_stack_end;            \
                                                ULONG   tx_thread_module_stack_size;            \
                                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m33-using-ac6"></a><span data-ttu-id="11426-426">AC6을 사용하는 Cortex-M33의 모듈 관리자 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-426">Building Module Manager for Cortex-M33 using AC6</span></span>

<span data-ttu-id="11426-427">예제 작업 영역이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="11426-427">An example workspace is provided.</span></span> <span data-ttu-id="11426-428">ThreadX 라이브러리, ThreadX 모듈 라이브러리, sample_threadx_module 프로젝트 및 demo_threadx_non-secure_zone 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="11426-428">Build the ThreadX library, ThreadX Modules library, sample_threadx_module project, and demo_threadx_non-secure_zone project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m33-using-ac6"></a><span data-ttu-id="11426-429">AC6을 사용하는 Cortex-M33의 외부 메모리 사용 API에 대한 특성</span><span class="sxs-lookup"><span data-stu-id="11426-429">Attributes for external memory enable API for Cortex-M33 using AC6</span></span>

| <span data-ttu-id="11426-430">특성 매개 변수</span><span class="sxs-lookup"><span data-stu-id="11426-430">Attribute parameter</span></span> |
|---|
| <span data-ttu-id="11426-431">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="11426-431">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span></span> |
| <span data-ttu-id="11426-432">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="11426-432">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span></span> |
| <span data-ttu-id="11426-433">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="11426-433">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span></span> |
| <span data-ttu-id="11426-434">TXM_MODULE_ATTRIBUTE_READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="11426-434">TXM_MODULE_ATTRIBUTE_READ_WRITE</span></span> |
| <span data-ttu-id="11426-435">TXM_MODULE_ATTRIBUTE_READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="11426-435">TXM_MODULE_ATTRIBUTE_READ_ONLY</span></span> |

### <a name="cortex-m33-using-gnu"></a><span data-ttu-id="11426-436">GNU를 사용하는 Cortex-M33</span><span class="sxs-lookup"><span data-stu-id="11426-436">Cortex-M33 using GNU</span></span>

#### <a name="module-preamble-for-cortex-m33-using-gnu"></a><span data-ttu-id="11426-437">GNU를 사용하는 Cortex-M33의 모듈 머리말</span><span class="sxs-lookup"><span data-stu-id="11426-437">Module preamble for Cortex-M33 using GNU</span></span>

#### <a name="module-properties-for-cortex-m33-using-gnu"></a><span data-ttu-id="11426-438">GNU를 사용하는 Cortex-M33의 모듈 속성</span><span class="sxs-lookup"><span data-stu-id="11426-438">Module properties for Cortex-M33 using GNU</span></span>

| <span data-ttu-id="11426-439">bit</span><span class="sxs-lookup"><span data-stu-id="11426-439">Bit</span></span> | <span data-ttu-id="11426-440">값</span><span class="sxs-lookup"><span data-stu-id="11426-440">Value</span></span> | <span data-ttu-id="11426-441">의미</span><span class="sxs-lookup"><span data-stu-id="11426-441">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="11426-442">0</span><span class="sxs-lookup"><span data-stu-id="11426-442">0</span></span> | <span data-ttu-id="11426-443">0</span><span class="sxs-lookup"><span data-stu-id="11426-443">0</span></span><br /><span data-ttu-id="11426-444">1</span><span class="sxs-lookup"><span data-stu-id="11426-444">1</span></span> | <span data-ttu-id="11426-445">권한 있는 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-445">Privileged mode execution</span></span><br /><span data-ttu-id="11426-446">사용자 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-446">User mode execution</span></span> |
| <span data-ttu-id="11426-447">1</span><span class="sxs-lookup"><span data-stu-id="11426-447">1</span></span> | <span data-ttu-id="11426-448">0</span><span class="sxs-lookup"><span data-stu-id="11426-448">0</span></span><br /><span data-ttu-id="11426-449">1</span><span class="sxs-lookup"><span data-stu-id="11426-449">1</span></span> | <span data-ttu-id="11426-450">MPU 보호 없음</span><span class="sxs-lookup"><span data-stu-id="11426-450">No MPU protection</span></span><br /><span data-ttu-id="11426-451">MPU 보호(사용자 모드가 선택되어 있어야 함)</span><span class="sxs-lookup"><span data-stu-id="11426-451">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="11426-452">2</span><span class="sxs-lookup"><span data-stu-id="11426-452">2</span></span> | <span data-ttu-id="11426-453">0</span><span class="sxs-lookup"><span data-stu-id="11426-453">0</span></span><br /><span data-ttu-id="11426-454">1</span><span class="sxs-lookup"><span data-stu-id="11426-454">1</span></span> | <span data-ttu-id="11426-455">공유/외부 메모리 액세스 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="11426-455">Disable shared/external memory access</span></span><br /><span data-ttu-id="11426-456">공유/외부 메모리 액세스 사용</span><span class="sxs-lookup"><span data-stu-id="11426-456">Enable shared/external memory access</span></span> |
| <span data-ttu-id="11426-457">[23-3]</span><span class="sxs-lookup"><span data-stu-id="11426-457">[23-3]</span></span> | <span data-ttu-id="11426-458">0</span><span class="sxs-lookup"><span data-stu-id="11426-458">0</span></span> | <span data-ttu-id="11426-459">예약됨</span><span class="sxs-lookup"><span data-stu-id="11426-459">Reserved</span></span>
| <span data-ttu-id="11426-460">[31-24]</span><span class="sxs-lookup"><span data-stu-id="11426-460">[31-24]</span></span> | <br /><span data-ttu-id="11426-461">0x00</span><span class="sxs-lookup"><span data-stu-id="11426-461">0x00</span></span><br /><span data-ttu-id="11426-462">0x01</span><span class="sxs-lookup"><span data-stu-id="11426-462">0x01</span></span><br /><span data-ttu-id="11426-463">0x02</span><span class="sxs-lookup"><span data-stu-id="11426-463">0x02</span></span> | <span data-ttu-id="11426-464">**컴파일러 ID**</span><span class="sxs-lookup"><span data-stu-id="11426-464">**Compiler ID**</span></span><br /><span data-ttu-id="11426-465">IAR</span><span class="sxs-lookup"><span data-stu-id="11426-465">IAR</span></span><br /><span data-ttu-id="11426-466">ARM</span><span class="sxs-lookup"><span data-stu-id="11426-466">ARM</span></span><br /><span data-ttu-id="11426-467">GNU</span><span class="sxs-lookup"><span data-stu-id="11426-467">GNU</span></span> |

#### <a name="module-linker-for-cortex-m33-using-gnu"></a><span data-ttu-id="11426-468">GNU를 사용하는 Cortex-M33의 모듈 링커</span><span class="sxs-lookup"><span data-stu-id="11426-468">Module linker for Cortex-M33 using GNU</span></span>

#### <a name="building-modules-for-cortex-m33-using-gnu"></a><span data-ttu-id="11426-469">GNU를 사용하는 Cortex-M33의 모듈 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-469">Building Modules for Cortex-M33 using GNU</span></span>

#### <a name="thread-extension-definition-for-cortex-m33-using-gnu"></a><span data-ttu-id="11426-470">GNU를 사용하는 Cortex-M33의 스레드 확장 정의</span><span class="sxs-lookup"><span data-stu-id="11426-470">Thread extension definition for Cortex-M33 using GNU</span></span>

#### <a name="building-module-manager-for-cortex-m33-using-gnu"></a><span data-ttu-id="11426-471">GNU를 사용하는 Cortex-M33의 모듈 관리자 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-471">Building Module Manager for Cortex-M33 using GNU</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m33-using-gnu"></a><span data-ttu-id="11426-472">GNU를 사용하는 Cortex-M33의 외부 메모리 사용 API에 대한 특성</span><span class="sxs-lookup"><span data-stu-id="11426-472">Attributes for external memory enable API for Cortex-M33 using GNU</span></span>

| <span data-ttu-id="11426-473">특성 매개 변수</span><span class="sxs-lookup"><span data-stu-id="11426-473">Attribute parameter</span></span> |
|---|
| <span data-ttu-id="11426-474">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="11426-474">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span></span> |
| <span data-ttu-id="11426-475">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="11426-475">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span></span> |
| <span data-ttu-id="11426-476">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="11426-476">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span></span> |
| <span data-ttu-id="11426-477">TXM_MODULE_ATTRIBUTE_READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="11426-477">TXM_MODULE_ATTRIBUTE_READ_WRITE</span></span> |
| <span data-ttu-id="11426-478">TXM_MODULE_ATTRIBUTE_READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="11426-478">TXM_MODULE_ATTRIBUTE_READ_ONLY</span></span> |

### <a name="cortex-m33-using-iar"></a><span data-ttu-id="11426-479">IAR을 사용하는 Cortex-M33</span><span class="sxs-lookup"><span data-stu-id="11426-479">Cortex-M33 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m33-using-iar"></a><span data-ttu-id="11426-480">IAR을 사용하는 Cortex-M33의 모듈 머리말</span><span class="sxs-lookup"><span data-stu-id="11426-480">Module preamble for Cortex-M33 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */

    PUBLIC __txm_module_preamble


    /* Define application-specific start/stop entry points for the module.  */

    EXTERN demo_module_start


    /* Define common external refrences.  */

    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        // Module ID
    DC32      0x6                                               // Module Major Version
    DC32      0x1                                               // Module Minor Version
    DC32      32                                                // Module Preamble Size in 32-bit words
    DC32      0x12345678                                        // Module ID (application defined)
    DC32      0x00000007                                        // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bits 23-3: Reserved
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
    DC32      _txm_module_thread_shell_entry - . - 0            // Module Shell Entry Point
    DC32      demo_module_start - . - 0                         // Module Start Thread Entry Point
    DC32      0                                                 // Module Stop Thread Entry Point
    DC32      1                                                 // Module Start/Stop Thread Priority
    DC32      1024                                              // Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 // Module Callback Thread Entry
    DC32      1                                                 // Module Callback Thread Priority
    DC32      1024                                              // Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      // Module Code Size
    DC32      RWPI$$Length                                      // Module Data Size
    DC32      0                                                 // Reserved 0
    DC32      0                                                 // Reserved 1
    DC32      0                                                 // Reserved 2
    DC32      0                                                 // Reserved 3
    DC32      0                                                 // Reserved 4
    DC32      0                                                 // Reserved 5
    DC32      0                                                 // Reserved 6
    DC32      0                                                 // Reserved 7
    DC32      0                                                 // Reserved 8
    DC32      0                                                 // Reserved 9
    DC32      0                                                 // Reserved 10
    DC32      0                                                 // Reserved 11
    DC32      0                                                 // Reserved 12
    DC32      0                                                 // Reserved 13
    DC32      0                                                 // Reserved 14
    DC32      0                                                 // Reserved 15

    END

```

#### <a name="module-properties-for-cortex-m33-using-iar"></a><span data-ttu-id="11426-481">IAR을 사용하는 Cortex-M33의 모듈 속성</span><span class="sxs-lookup"><span data-stu-id="11426-481">Module properties for Cortex-M33 using IAR</span></span>

| <span data-ttu-id="11426-482">bit</span><span class="sxs-lookup"><span data-stu-id="11426-482">Bit</span></span> | <span data-ttu-id="11426-483">값</span><span class="sxs-lookup"><span data-stu-id="11426-483">Value</span></span> | <span data-ttu-id="11426-484">의미</span><span class="sxs-lookup"><span data-stu-id="11426-484">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="11426-485">0</span><span class="sxs-lookup"><span data-stu-id="11426-485">0</span></span> | <span data-ttu-id="11426-486">0</span><span class="sxs-lookup"><span data-stu-id="11426-486">0</span></span><br /><span data-ttu-id="11426-487">1</span><span class="sxs-lookup"><span data-stu-id="11426-487">1</span></span> | <span data-ttu-id="11426-488">권한 있는 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-488">Privileged mode execution</span></span><br /><span data-ttu-id="11426-489">사용자 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-489">User mode execution</span></span> |
| <span data-ttu-id="11426-490">1</span><span class="sxs-lookup"><span data-stu-id="11426-490">1</span></span> | <span data-ttu-id="11426-491">0</span><span class="sxs-lookup"><span data-stu-id="11426-491">0</span></span><br /><span data-ttu-id="11426-492">1</span><span class="sxs-lookup"><span data-stu-id="11426-492">1</span></span> | <span data-ttu-id="11426-493">MPU 보호 없음</span><span class="sxs-lookup"><span data-stu-id="11426-493">No MPU protection</span></span><br /><span data-ttu-id="11426-494">MPU 보호(사용자 모드가 선택되어 있어야 함)</span><span class="sxs-lookup"><span data-stu-id="11426-494">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="11426-495">2</span><span class="sxs-lookup"><span data-stu-id="11426-495">2</span></span> | <span data-ttu-id="11426-496">0</span><span class="sxs-lookup"><span data-stu-id="11426-496">0</span></span><br /><span data-ttu-id="11426-497">1</span><span class="sxs-lookup"><span data-stu-id="11426-497">1</span></span> | <span data-ttu-id="11426-498">공유/외부 메모리 액세스 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="11426-498">Disable shared/external memory access</span></span><br /><span data-ttu-id="11426-499">공유/외부 메모리 액세스 사용</span><span class="sxs-lookup"><span data-stu-id="11426-499">Enable shared/external memory access</span></span> |
| <span data-ttu-id="11426-500">[23-3]</span><span class="sxs-lookup"><span data-stu-id="11426-500">[23-3]</span></span> | <span data-ttu-id="11426-501">0</span><span class="sxs-lookup"><span data-stu-id="11426-501">0</span></span> | <span data-ttu-id="11426-502">예약됨</span><span class="sxs-lookup"><span data-stu-id="11426-502">Reserved</span></span>
| <span data-ttu-id="11426-503">[31-24]</span><span class="sxs-lookup"><span data-stu-id="11426-503">[31-24]</span></span> | <br /><span data-ttu-id="11426-504">0x00</span><span class="sxs-lookup"><span data-stu-id="11426-504">0x00</span></span><br /><span data-ttu-id="11426-505">0x01</span><span class="sxs-lookup"><span data-stu-id="11426-505">0x01</span></span><br /><span data-ttu-id="11426-506">0x02</span><span class="sxs-lookup"><span data-stu-id="11426-506">0x02</span></span> | <span data-ttu-id="11426-507">**컴파일러 ID**</span><span class="sxs-lookup"><span data-stu-id="11426-507">**Compiler ID**</span></span><br /><span data-ttu-id="11426-508">IAR</span><span class="sxs-lookup"><span data-stu-id="11426-508">IAR</span></span><br /><span data-ttu-id="11426-509">ARM</span><span class="sxs-lookup"><span data-stu-id="11426-509">ARM</span></span><br /><span data-ttu-id="11426-510">GNU</span><span class="sxs-lookup"><span data-stu-id="11426-510">GNU</span></span> |

#### <a name="module-linker-for-cortex-m33-using-iar"></a><span data-ttu-id="11426-511">IAR을 사용하는 Cortex-M33의 모듈 링커</span><span class="sxs-lookup"><span data-stu-id="11426-511">Module linker for Cortex-M33 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\a_v1_0.xml" */
/*-Specials-*/
define symbol __ICFEDIT_intvec_start__ = 0x0;
/*-Memory Regions-*/
define symbol __ICFEDIT_region_ROM_start__ = 0x080f0000;
define symbol __ICFEDIT_region_ROM_end__   = 0x080fffff;
define symbol __ICFEDIT_region_RAM_start__ = 0x64002800;
define symbol __ICFEDIT_region_RAM_end__   = 0x64100000;
/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__   = 0;
define symbol __ICFEDIT_size_svcstack__ = 0;
define symbol __ICFEDIT_size_irqstack__ = 0;
define symbol __ICFEDIT_size_fiqstack__ = 0;
define symbol __ICFEDIT_size_undstack__ = 0;
define symbol __ICFEDIT_size_abtstack__ = 0;
define symbol __ICFEDIT_size_heap__     = 0x1000;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region ROM_region   = mem:[from __ICFEDIT_region_ROM_start__   to __ICFEDIT_region_ROM_end__];
define region RAM_region   = mem:[from __ICFEDIT_region_RAM_start__   to __ICFEDIT_region_RAM_end__];

//define block CSTACK    with alignment = 8, size = __ICFEDIT_size_cstack__   { };
//define block SVC_STACK with alignment = 8, size = __ICFEDIT_size_svcstack__ { };
//define block IRQ_STACK with alignment = 8, size = __ICFEDIT_size_irqstack__ { };
//define block FIQ_STACK with alignment = 8, size = __ICFEDIT_size_fiqstack__ { };
//define block UND_STACK with alignment = 8, size = __ICFEDIT_size_undstack__ { };
//define block ABT_STACK with alignment = 8, size = __ICFEDIT_size_abtstack__ { };
define block HEAP      with alignment = 8, size = __ICFEDIT_size_heap__     { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

//place at address mem:__ICFEDIT_intvec_start__ { readonly section .intvec };

define movable block ROPI with alignment = 4, fixed order 
{ 
  ro object txm_module_preamble.o,
  ro, 
  ro data 
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-m33-using-iar"></a><span data-ttu-id="11426-512">IAR을 사용하는 Cortex-M33의 모듈 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-512">Building Modules for Cortex-M33 using IAR</span></span>

#### <a name="thread-extension-definition-for-cortex-m33-using-iar"></a><span data-ttu-id="11426-513">IAR을 사용하는 Cortex-M33의 스레드 확장 정의</span><span class="sxs-lookup"><span data-stu-id="11426-513">Thread extension definition for Cortex-M33 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2                   VOID    *tx_thread_module_instance_ptr;         \
                                                VOID    *tx_thread_module_entry_info_ptr;       \
                                                ULONG   tx_thread_module_current_user_mode;     \
                                                ULONG   tx_thread_module_user_mode;             \
                                                ULONG   tx_thread_module_saved_lr;              \
                                                VOID    *tx_thread_module_kernel_stack_start;   \
                                                VOID    *tx_thread_module_kernel_stack_end;     \
                                                ULONG   tx_thread_module_kernel_stack_size;     \
                                                VOID    *tx_thread_module_stack_ptr;            \
                                                VOID    *tx_thread_module_stack_start;          \
                                                VOID    *tx_thread_module_stack_end;            \
                                                ULONG   tx_thread_module_stack_size;            \
                                                VOID    *tx_thread_module_reserved;             \
                                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-m33-using-iar"></a><span data-ttu-id="11426-514">IAR을 사용하는 Cortex-M33의 모듈 관리자 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-514">Building Module Manager for Cortex-M33 using IAR</span></span>

<span data-ttu-id="11426-515">예제 작업 영역이 아직 제공되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-515">An example workspace is not yet provided.</span></span> <span data-ttu-id="11426-516">곧 제공될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="11426-516">Coming soon.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m33-using-iar"></a><span data-ttu-id="11426-517">IAR을 사용하는 Cortex-M33의 외부 메모리 사용 API에 대한 특성</span><span class="sxs-lookup"><span data-stu-id="11426-517">Attributes for external memory enable API for Cortex-M33 using IAR</span></span>

| <span data-ttu-id="11426-518">특성 매개 변수</span><span class="sxs-lookup"><span data-stu-id="11426-518">Attribute parameter</span></span> |
|---|
| <span data-ttu-id="11426-519">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="11426-519">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span></span> |
| <span data-ttu-id="11426-520">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="11426-520">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span></span> |
| <span data-ttu-id="11426-521">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="11426-521">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span></span> |
| <span data-ttu-id="11426-522">TXM_MODULE_ATTRIBUTE_READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="11426-522">TXM_MODULE_ATTRIBUTE_READ_WRITE</span></span> |
| <span data-ttu-id="11426-523">TXM_MODULE_ATTRIBUTE_READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="11426-523">TXM_MODULE_ATTRIBUTE_READ_ONLY</span></span> |

## <a name="cortex-m4-processor"></a><span data-ttu-id="11426-524">Cortex-M4 프로세서</span><span class="sxs-lookup"><span data-stu-id="11426-524">Cortex-M4 processor</span></span>

### <a name="cortex-m4-using-ac5"></a><span data-ttu-id="11426-525">AC5를 사용하는 Cortex-M4</span><span class="sxs-lookup"><span data-stu-id="11426-525">Cortex-M4 using AC5</span></span>

#### <a name="module-preamble-for-cortex-m4-using-ac5"></a><span data-ttu-id="11426-526">AC5를 사용하는 Cortex-M4의 모듈 머리말</span><span class="sxs-lookup"><span data-stu-id="11426-526">Module preamble for Cortex-M4 using AC5</span></span>

```armasm
    AREA Init, CODE, READONLY

    PRESERVE8

    /* Define public symbols.  */

    EXPORT __txm_module_preamble

    ; Define application-specific start/stop entry points for the module

    EXTERN demo_module_start

    /* Define common external references.  */

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|
    IMPORT  |Image$$ER_RW$$Length|
    IMPORT  |Image$$ER_RW$$RW$$Length|
    IMPORT  |Image$$ER_RW$$ZI$$Length|
    IMPORT  |Image$$ER_ZI$$ZI$$Length|

__txm_module_preamble
    DCD     0x4D4F4455                                          // Module ID
    DCD     0x6                                                 // Module Major Version
    DCD     0x1                                                 // Module Minor Version
    DCD     32                                                  // Module Preamble Size in 32-bit words
    DCD     0x12345678                                          // Module ID (application defined)
    DCD     0x01000007                                          // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bits 23-3: Reserved
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
    DCD     _txm_module_thread_shell_entry - __txm_module_preamble              // Module Shell Entry Point
    DCD     demo_module_start - __txm_module_preamble           // Module Start Thread Entry Point
    DCD     0                                                   // Module Stop Thread Entry Point
    DCD     1                                                   // Module Start/Stop Thread Priority
    DCD     1024                                                // Module Start/Stop Thread Stack Size
    DCD     _txm_module_callback_request_thread_entry - __txm_module_preamble   // Module Callback Thread Entry
    DCD     1                                                   // Module Callback Thread Priority
    DCD     1024                                                // Module Callback Thread Stack Size
    DCD     |Image$$ER_RO$$Length| + |Image$$ER_RW$$Length|     // Module Code Size
    DCD     |Image$$ER_RW$$Length| + |Image$$ER_ZI$$ZI$$Length| // Module Data Size
    DCD     0                                                   // Reserved 0
    DCD     0                                                   // Reserved 1
    DCD     0                                                   // Reserved 2
    DCD     0                                                   // Reserved 3
    DCD     0                                                   // Reserved 4
    DCD     0                                                   // Reserved 5
    DCD     0                                                   // Reserved 6
    DCD     0                                                   // Reserved 7
    DCD     0                                                   // Reserved 8
    DCD     0                                                   // Reserved 9
    DCD     0                                                   // Reserved 10
    DCD     0                                                   // Reserved 11
    DCD     0                                                   // Reserved 12
    DCD     0                                                   // Reserved 13
    DCD     0                                                   // Reserved 14
    DCD     0                                                   // Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m4-using-ac5"></a><span data-ttu-id="11426-527">AC5를 사용하는 Cortex-M4의 모듈 속성</span><span class="sxs-lookup"><span data-stu-id="11426-527">Module properties for Cortex-M4 using AC5</span></span>

| <span data-ttu-id="11426-528">bit</span><span class="sxs-lookup"><span data-stu-id="11426-528">Bit</span></span> | <span data-ttu-id="11426-529">값</span><span class="sxs-lookup"><span data-stu-id="11426-529">Value</span></span> | <span data-ttu-id="11426-530">의미</span><span class="sxs-lookup"><span data-stu-id="11426-530">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="11426-531">0</span><span class="sxs-lookup"><span data-stu-id="11426-531">0</span></span> | <span data-ttu-id="11426-532">0</span><span class="sxs-lookup"><span data-stu-id="11426-532">0</span></span><br /><span data-ttu-id="11426-533">1</span><span class="sxs-lookup"><span data-stu-id="11426-533">1</span></span> | <span data-ttu-id="11426-534">권한 있는 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-534">Privileged mode execution</span></span><br /><span data-ttu-id="11426-535">사용자 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-535">User mode execution</span></span> |
| <span data-ttu-id="11426-536">1</span><span class="sxs-lookup"><span data-stu-id="11426-536">1</span></span> | <span data-ttu-id="11426-537">0</span><span class="sxs-lookup"><span data-stu-id="11426-537">0</span></span><br /><span data-ttu-id="11426-538">1</span><span class="sxs-lookup"><span data-stu-id="11426-538">1</span></span> | <span data-ttu-id="11426-539">MPU 보호 없음</span><span class="sxs-lookup"><span data-stu-id="11426-539">No MPU protection</span></span><br /><span data-ttu-id="11426-540">MPU 보호(사용자 모드가 선택되어 있어야 함)</span><span class="sxs-lookup"><span data-stu-id="11426-540">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="11426-541">2</span><span class="sxs-lookup"><span data-stu-id="11426-541">2</span></span> | <span data-ttu-id="11426-542">0</span><span class="sxs-lookup"><span data-stu-id="11426-542">0</span></span><br /><span data-ttu-id="11426-543">1</span><span class="sxs-lookup"><span data-stu-id="11426-543">1</span></span> | <span data-ttu-id="11426-544">공유/외부 메모리 액세스 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="11426-544">Disable shared/external memory access</span></span><br /><span data-ttu-id="11426-545">공유/외부 메모리 액세스 사용</span><span class="sxs-lookup"><span data-stu-id="11426-545">Enable shared/external memory access</span></span> |
| <span data-ttu-id="11426-546">[23-3]</span><span class="sxs-lookup"><span data-stu-id="11426-546">[23-3]</span></span> | <span data-ttu-id="11426-547">0</span><span class="sxs-lookup"><span data-stu-id="11426-547">0</span></span> | <span data-ttu-id="11426-548">예약됨</span><span class="sxs-lookup"><span data-stu-id="11426-548">Reserved</span></span>
| <span data-ttu-id="11426-549">[31-24]</span><span class="sxs-lookup"><span data-stu-id="11426-549">[31-24]</span></span> | <br /><span data-ttu-id="11426-550">0x00</span><span class="sxs-lookup"><span data-stu-id="11426-550">0x00</span></span><br /><span data-ttu-id="11426-551">0x01</span><span class="sxs-lookup"><span data-stu-id="11426-551">0x01</span></span><br /><span data-ttu-id="11426-552">0x02</span><span class="sxs-lookup"><span data-stu-id="11426-552">0x02</span></span> | <span data-ttu-id="11426-553">**컴파일러 ID**</span><span class="sxs-lookup"><span data-stu-id="11426-553">**Compiler ID**</span></span><br /><span data-ttu-id="11426-554">IAR</span><span class="sxs-lookup"><span data-stu-id="11426-554">IAR</span></span><br /><span data-ttu-id="11426-555">ARM</span><span class="sxs-lookup"><span data-stu-id="11426-555">ARM</span></span><br /><span data-ttu-id="11426-556">GNU</span><span class="sxs-lookup"><span data-stu-id="11426-556">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-ac5"></a><span data-ttu-id="11426-557">AC5를 사용하는 Cortex-M4의 모듈 링커</span><span class="sxs-lookup"><span data-stu-id="11426-557">Module linker for Cortex-M4 using AC5</span></span>

<span data-ttu-id="11426-558">예제 링커 파일은 제공되지 않으며 명령줄에서 링크가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="11426-558">No example linker file is provided; linking is done on the command line.</span></span> <span data-ttu-id="11426-559">다음 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="11426-559">See next section.</span></span>

#### <a name="building-modules-for-cortex-m4-using-ac5"></a><span data-ttu-id="11426-560">AC5를 사용하는 Cortex-M4의 모듈 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-560">Building Modules for Cortex-M4 using AC5</span></span>

<span data-ttu-id="11426-561">build_threadx_module_demo.bat 예제를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="11426-561">See example build_threadx_module_demo.bat:</span></span>

```dos
armasm -g --cpreproc --cpu=cortex-m4 --fpu=vfpv4 --apcs=/interwork/ropi/rwpi txm_module_preamble.S
armcc  -g --cpu=cortex-m4 --fpu=vfpv4 -c --apcs=/interwork/ropi/rwpi --lower_ropi -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module.c
armlink -d -o sample_threadx_module.axf --elf --ro=0x30000 --rw=0x40000 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list sample_threadx_module.map txm_module_preamble.o sample_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-m4-using-ac5"></a><span data-ttu-id="11426-562">AC5를 사용하는 Cortex-M4의 스레드 확장 정의</span><span class="sxs-lookup"><span data-stu-id="11426-562">Thread extension definition for Cortex-M4 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m4-using-ac5"></a><span data-ttu-id="11426-563">AC5를 사용하는 Cortex-M4의 모듈 관리자 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-563">Building Module Manager for Cortex-M4 using AC5</span></span>

<span data-ttu-id="11426-564">build_threadx_module_manager_demo.bat 예제를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="11426-564">See example build_threadx_module_manager_demo.bat:</span></span>

```dos
armasm -g --cpreproc --cpu=cortex-m4 --fpu=vfpv4 --apcs=/interwork tx_initialize_low_level.S
armcc -g --cpu=cortex-m4 --fpu=vfpv4 -c -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module_manager.c
armlink -d -o sample_threadx_module_manager.axf --elf --ro 0x00000000 --first tx_initialize_low_level.o(RESET) --remove --map --symbols --list sample_threadx_module_manager.map tx_initialize_low_level.o sample_threadx_module_manager.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-ac5"></a><span data-ttu-id="11426-565">AC5를 사용하는 Cortex-M4의 외부 메모리 사용 API에 대한 특성</span><span class="sxs-lookup"><span data-stu-id="11426-565">Attributes for external memory enable API for Cortex-M4 using AC5</span></span>

<span data-ttu-id="11426-566">모듈에는 항상 공유 메모리에 대한 읽기 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-566">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="11426-567">특성 매개 변수</span><span class="sxs-lookup"><span data-stu-id="11426-567">Attribute parameter</span></span> | <span data-ttu-id="11426-568">의미</span><span class="sxs-lookup"><span data-stu-id="11426-568">Meaning</span></span> |
|---|---|
| <span data-ttu-id="11426-569">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="11426-569">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="11426-570">쓰기 액세스</span><span class="sxs-lookup"><span data-stu-id="11426-570">Write access</span></span> |

### <a name="cortex-m4-using-ac6"></a><span data-ttu-id="11426-571">AC6을 사용하는 Cortex-M4</span><span class="sxs-lookup"><span data-stu-id="11426-571">Cortex-M4 using AC6</span></span>

#### <a name="module-preamble-for-cortex-m4-using-ac6"></a><span data-ttu-id="11426-572">AC6을 사용하는 Cortex-M4의 모듈 머리말</span><span class="sxs-lookup"><span data-stu-id="11426-572">Module preamble for Cortex-M4 using AC6</span></span>

```armasm
    .text
    .align 4
    .syntax unified
    .section Init
    
    // Define public symbols
    .global __txm_module_preamble

    // Define application-specific start/stop entry points for the module
    .global demo_module_start

    // Define common external references
    .global  _txm_module_thread_shell_entry
    .global  _txm_module_callback_request_thread_entry

    .eabi_attribute Tag_ABI_PCS_RO_data, 1
    .eabi_attribute Tag_ABI_PCS_R9_use,  1
    .eabi_attribute Tag_ABI_PCS_RW_data, 2

__txm_module_preamble:
    .dc.l   0x4D4F4455                                          // Module ID
    .dc.l   0x6                                                 // Module Major Version
    .dc.l   0x1                                                 // Module Minor Version
    .dc.l   32                                                  // Module Preamble Size in 32-bit words
    .dc.l   0x12345678                                          // Module ID (application defined)
    .dc.l   0x01000007                                          // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    .dc.l   _txm_module_thread_shell_entry - __txm_module_preamble // Module Shell Entry Point
    .dc.l   demo_module_start - __txm_module_preamble           // Module Start Thread Entry Point
    .dc.l   0                                                   // Module Stop Thread Entry Point
    .dc.l   1                                                   // Module Start/Stop Thread Priority
    .dc.l   1024                                                // Module Start/Stop Thread Stack Size
    .dc.l   _txm_module_callback_request_thread_entry - __txm_module_preamble // Module Callback Thread Entry
    .dc.l   1                                                   // Module Callback Thread Priority
    .dc.l   1024                                                // Module Callback Thread Stack Size
    .dc.l   0x10000                                             // Module Code Size
    .dc.l   0x10000                                             // Module Data Size
    .dc.l   0                                                   // Reserved 0
    .dc.l   0                                                   // Reserved 1
    .dc.l   0                                                   // Reserved 2
    .dc.l   0                                                   // Reserved 3
    .dc.l   0                                                   // Reserved 4
    .dc.l   0                                                   // Reserved 5
    .dc.l   0                                                   // Reserved 6
    .dc.l   0                                                   // Reserved 7
    .dc.l   0                                                   // Reserved 8
    .dc.l   0                                                   // Reserved 9
    .dc.l   0                                                   // Reserved 10
    .dc.l   0                                                   // Reserved 11
    .dc.l   0                                                   // Reserved 12
    .dc.l   0                                                   // Reserved 13
    .dc.l   0                                                   // Reserved 14
    .dc.l   0                                                   // Reserved 15
```

#### <a name="module-properties-for-cortex-m4-using-ac6"></a><span data-ttu-id="11426-573">AC6을 사용하는 Cortex-M4의 모듈 속성</span><span class="sxs-lookup"><span data-stu-id="11426-573">Module properties for Cortex-M4 using AC6</span></span>

| <span data-ttu-id="11426-574">bit</span><span class="sxs-lookup"><span data-stu-id="11426-574">Bit</span></span> | <span data-ttu-id="11426-575">값</span><span class="sxs-lookup"><span data-stu-id="11426-575">Value</span></span> | <span data-ttu-id="11426-576">의미</span><span class="sxs-lookup"><span data-stu-id="11426-576">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="11426-577">0</span><span class="sxs-lookup"><span data-stu-id="11426-577">0</span></span> | <span data-ttu-id="11426-578">0</span><span class="sxs-lookup"><span data-stu-id="11426-578">0</span></span><br /><span data-ttu-id="11426-579">1</span><span class="sxs-lookup"><span data-stu-id="11426-579">1</span></span> | <span data-ttu-id="11426-580">권한 있는 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-580">Privileged mode execution</span></span><br /><span data-ttu-id="11426-581">사용자 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-581">User mode execution</span></span> |
| <span data-ttu-id="11426-582">1</span><span class="sxs-lookup"><span data-stu-id="11426-582">1</span></span> | <span data-ttu-id="11426-583">0</span><span class="sxs-lookup"><span data-stu-id="11426-583">0</span></span><br /><span data-ttu-id="11426-584">1</span><span class="sxs-lookup"><span data-stu-id="11426-584">1</span></span> | <span data-ttu-id="11426-585">MPU 보호 없음</span><span class="sxs-lookup"><span data-stu-id="11426-585">No MPU protection</span></span><br /><span data-ttu-id="11426-586">MPU 보호(사용자 모드가 선택되어 있어야 함)</span><span class="sxs-lookup"><span data-stu-id="11426-586">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="11426-587">2</span><span class="sxs-lookup"><span data-stu-id="11426-587">2</span></span> | <span data-ttu-id="11426-588">0</span><span class="sxs-lookup"><span data-stu-id="11426-588">0</span></span><br /><span data-ttu-id="11426-589">1</span><span class="sxs-lookup"><span data-stu-id="11426-589">1</span></span> | <span data-ttu-id="11426-590">공유/외부 메모리 액세스 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="11426-590">Disable shared/external memory access</span></span><br /><span data-ttu-id="11426-591">공유/외부 메모리 액세스 사용</span><span class="sxs-lookup"><span data-stu-id="11426-591">Enable shared/external memory access</span></span> |
| <span data-ttu-id="11426-592">[23-3]</span><span class="sxs-lookup"><span data-stu-id="11426-592">[23-3]</span></span> | <span data-ttu-id="11426-593">0</span><span class="sxs-lookup"><span data-stu-id="11426-593">0</span></span> | <span data-ttu-id="11426-594">예약됨</span><span class="sxs-lookup"><span data-stu-id="11426-594">Reserved</span></span>
| <span data-ttu-id="11426-595">[31-24]</span><span class="sxs-lookup"><span data-stu-id="11426-595">[31-24]</span></span> | <br /><span data-ttu-id="11426-596">0x00</span><span class="sxs-lookup"><span data-stu-id="11426-596">0x00</span></span><br /><span data-ttu-id="11426-597">0x01</span><span class="sxs-lookup"><span data-stu-id="11426-597">0x01</span></span><br /><span data-ttu-id="11426-598">0x02</span><span class="sxs-lookup"><span data-stu-id="11426-598">0x02</span></span> | <span data-ttu-id="11426-599">**컴파일러 ID**</span><span class="sxs-lookup"><span data-stu-id="11426-599">**Compiler ID**</span></span><br /><span data-ttu-id="11426-600">IAR</span><span class="sxs-lookup"><span data-stu-id="11426-600">IAR</span></span><br /><span data-ttu-id="11426-601">ARM</span><span class="sxs-lookup"><span data-stu-id="11426-601">ARM</span></span><br /><span data-ttu-id="11426-602">GNU</span><span class="sxs-lookup"><span data-stu-id="11426-602">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-ac6"></a><span data-ttu-id="11426-603">AC6을 사용하는 Cortex-M4의 모듈 링커</span><span class="sxs-lookup"><span data-stu-id="11426-603">Module linker for Cortex-M4 using AC6</span></span>

<span data-ttu-id="11426-604">링커 파일이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-604">No linker file is used.</span></span> <span data-ttu-id="11426-605">프로젝트 설정을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="11426-605">See project settings.</span></span>

#### <a name="building-modules-for-cortex-m4-using-ac6"></a><span data-ttu-id="11426-606">AC6을 사용하는 Cortex-M4의 모듈 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-606">Building Modules for Cortex-M4 using AC6</span></span>

<span data-ttu-id="11426-607">예제 작업 영역이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="11426-607">An example workspace is provided.</span></span> <span data-ttu-id="11426-608">ThreadX 라이브러리, ThreadX 모듈 라이브러리, 샘플 모듈 프로젝트 및 샘플 모듈 관리자 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="11426-608">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m4-using-ac6"></a><span data-ttu-id="11426-609">AC6을 사용하는 Cortex-M4의 스레드 확장 정의</span><span class="sxs-lookup"><span data-stu-id="11426-609">Thread extension definition for Cortex-M4 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m4-using-ac6"></a><span data-ttu-id="11426-610">AC6을 사용하는 Cortex-M4의 모듈 관리자 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-610">Building Module Manager for Cortex-M4 using AC6</span></span>

<span data-ttu-id="11426-611">예제 작업 영역이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="11426-611">An example workspace is provided.</span></span> <span data-ttu-id="11426-612">ThreadX 라이브러리, ThreadX 모듈 라이브러리, 샘플 모듈 프로젝트 및 샘플 모듈 관리자 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="11426-612">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-ac6"></a><span data-ttu-id="11426-613">AC6을 사용하는 Cortex-M4의 외부 메모리 사용 API에 대한 특성</span><span class="sxs-lookup"><span data-stu-id="11426-613">Attributes for external memory enable API for Cortex-M4 using AC6</span></span>

<span data-ttu-id="11426-614">모듈에는 항상 공유 메모리에 대한 읽기 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-614">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="11426-615">특성 매개 변수</span><span class="sxs-lookup"><span data-stu-id="11426-615">Attribute parameter</span></span> | <span data-ttu-id="11426-616">의미</span><span class="sxs-lookup"><span data-stu-id="11426-616">Meaning</span></span> |
|---|---|
| <span data-ttu-id="11426-617">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="11426-617">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="11426-618">쓰기 액세스</span><span class="sxs-lookup"><span data-stu-id="11426-618">Write access</span></span> |

### <a name="cortex-m4-using-gnu"></a><span data-ttu-id="11426-619">GNU를 사용하는 Cortex-M4</span><span class="sxs-lookup"><span data-stu-id="11426-619">Cortex-M4 using GNU</span></span>

#### <a name="module-preamble-for-cortex-m4-using-gnu"></a><span data-ttu-id="11426-620">GNU를 사용하는 Cortex-M4의 모듈 머리말</span><span class="sxs-lookup"><span data-stu-id="11426-620">Module preamble for Cortex-M4 using GNU</span></span>

```armasm
    .text
    .align 4
    .syntax unified

    /* Define public symbols.  */
    .global __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    .global demo_module_start

    /* Define common external refrences.  */
    .global _txm_module_thread_shell_entry
    .global _txm_module_callback_request_thread_entry

__txm_module_preamble:
    .dc.l      0x4D4F4455                                       // Module ID
    .dc.l      0x6                                              // Module Major Version
    .dc.l      0x1                                              // Module Minor Version
    .dc.l      32                                               // Module Preamble Size in 32-bit words
    .dc.l      0x12345678                                       // Module ID (application defined)
    .dc.l      0x02000007                                       // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bits 23-3: Reserved
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
    .dc.l      _txm_module_thread_shell_entry - . - 0           // Module Shell Entry Point
    .dc.l      demo_module_start - . - 0                        // Module Start Thread Entry Point
    .dc.l      0                                                // Module Stop Thread Entry Point 
    .dc.l      1                                                // Module Start/Stop Thread Priority
    .dc.l      1024                                             // Module Start/Stop Thread Stack Size
    .dc.l      _txm_module_callback_request_thread_entry - . - 0 // Module Callback Thread Entry
    .dc.l      1                                                // Module Callback Thread Priority
    .dc.l      1024                                             // Module Callback Thread Stack Size
    .dc.l      __code_size__                                    // Module Code Size
    .dc.l      __data_size__                                    // Module Data Size
    .dc.l      0                                                // Reserved 0
    .dc.l      0                                                // Reserved 1
    .dc.l      0                                                // Reserved 2
    .dc.l      0                                                // Reserved 3
    .dc.l      0                                                // Reserved 4
    .dc.l      0                                                // Reserved 5
    .dc.l      0                                                // Reserved 6
    .dc.l      0                                                // Reserved 7
    .dc.l      0                                                // Reserved 8
    .dc.l      0                                                // Reserved 9
    .dc.l      0                                                // Reserved 10
    .dc.l      0                                                // Reserved 11
    .dc.l      0                                                // Reserved 12
    .dc.l      0                                                // Reserved 13
    .dc.l      0                                                // Reserved 14
    .dc.l      0                                                // Reserved 15
```

#### <a name="module-properties-for-cortex-m4-using-gnu"></a><span data-ttu-id="11426-621">GNU를 사용하는 Cortex-M4의 모듈 속성</span><span class="sxs-lookup"><span data-stu-id="11426-621">Module properties for Cortex-M4 using GNU</span></span>

| <span data-ttu-id="11426-622">bit</span><span class="sxs-lookup"><span data-stu-id="11426-622">Bit</span></span> | <span data-ttu-id="11426-623">값</span><span class="sxs-lookup"><span data-stu-id="11426-623">Value</span></span> | <span data-ttu-id="11426-624">의미</span><span class="sxs-lookup"><span data-stu-id="11426-624">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="11426-625">0</span><span class="sxs-lookup"><span data-stu-id="11426-625">0</span></span> | <span data-ttu-id="11426-626">0</span><span class="sxs-lookup"><span data-stu-id="11426-626">0</span></span><br /><span data-ttu-id="11426-627">1</span><span class="sxs-lookup"><span data-stu-id="11426-627">1</span></span> | <span data-ttu-id="11426-628">권한 있는 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-628">Privileged mode execution</span></span><br /><span data-ttu-id="11426-629">사용자 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-629">User mode execution</span></span> |
| <span data-ttu-id="11426-630">1</span><span class="sxs-lookup"><span data-stu-id="11426-630">1</span></span> | <span data-ttu-id="11426-631">0</span><span class="sxs-lookup"><span data-stu-id="11426-631">0</span></span><br /><span data-ttu-id="11426-632">1</span><span class="sxs-lookup"><span data-stu-id="11426-632">1</span></span> | <span data-ttu-id="11426-633">MPU 보호 없음</span><span class="sxs-lookup"><span data-stu-id="11426-633">No MPU protection</span></span><br /><span data-ttu-id="11426-634">MPU 보호(사용자 모드가 선택되어 있어야 함)</span><span class="sxs-lookup"><span data-stu-id="11426-634">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="11426-635">2</span><span class="sxs-lookup"><span data-stu-id="11426-635">2</span></span> | <span data-ttu-id="11426-636">0</span><span class="sxs-lookup"><span data-stu-id="11426-636">0</span></span><br /><span data-ttu-id="11426-637">1</span><span class="sxs-lookup"><span data-stu-id="11426-637">1</span></span> | <span data-ttu-id="11426-638">공유/외부 메모리 액세스 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="11426-638">Disable shared/external memory access</span></span><br /><span data-ttu-id="11426-639">공유/외부 메모리 액세스 사용</span><span class="sxs-lookup"><span data-stu-id="11426-639">Enable shared/external memory access</span></span> |
| <span data-ttu-id="11426-640">[23-3]</span><span class="sxs-lookup"><span data-stu-id="11426-640">[23-3]</span></span> | <span data-ttu-id="11426-641">0</span><span class="sxs-lookup"><span data-stu-id="11426-641">0</span></span> | <span data-ttu-id="11426-642">예약됨</span><span class="sxs-lookup"><span data-stu-id="11426-642">Reserved</span></span>
| <span data-ttu-id="11426-643">[31-24]</span><span class="sxs-lookup"><span data-stu-id="11426-643">[31-24]</span></span> | <br /><span data-ttu-id="11426-644">0x00</span><span class="sxs-lookup"><span data-stu-id="11426-644">0x00</span></span><br /><span data-ttu-id="11426-645">0x01</span><span class="sxs-lookup"><span data-stu-id="11426-645">0x01</span></span><br /><span data-ttu-id="11426-646">0x02</span><span class="sxs-lookup"><span data-stu-id="11426-646">0x02</span></span> | <span data-ttu-id="11426-647">**컴파일러 ID**</span><span class="sxs-lookup"><span data-stu-id="11426-647">**Compiler ID**</span></span><br /><span data-ttu-id="11426-648">IAR</span><span class="sxs-lookup"><span data-stu-id="11426-648">IAR</span></span><br /><span data-ttu-id="11426-649">ARM</span><span class="sxs-lookup"><span data-stu-id="11426-649">ARM</span></span><br /><span data-ttu-id="11426-650">GNU</span><span class="sxs-lookup"><span data-stu-id="11426-650">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-gnu"></a><span data-ttu-id="11426-651">GNU를 사용하는 Cortex-M4의 모듈 링커</span><span class="sxs-lookup"><span data-stu-id="11426-651">Module linker for Cortex-M4 using GNU</span></span>

```c
MEMORY
{
  FLASH (rx) : ORIGIN = 0x00030000, LENGTH = 0x00010000
  RAM   (wx) : ORIGIN = 0, LENGTH = 0x00100000
}


SECTIONS
{
  __FLASH_segment_start__ = 0x00030000;
  __FLASH_segment_end__   = 0x00040000;
  __RAM_segment_start__   = 0;
  __RAM_segment_end__     = 0x8000;

  __HEAPSIZE__ = 128;

  __preamble_load_start__ = __FLASH_segment_start__;
  .preamble __FLASH_segment_start__ : AT(__FLASH_segment_start__)
  {
    __preamble_start__ = .;
    *(.preamble .preamble.*)
  }
  __preamble_end__ = __preamble_start__ + SIZEOF(.preamble);

  __dynsym_load_start__ =  ALIGN(__preamble_end__ , 4);
  .dynsym ALIGN(__dynsym_load_start__ , 4) : AT(ALIGN(__dynsym_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynsym))
    KEEP (*(.dynsym*))
    . = ALIGN(4);
  }
  __dynsym_end__ = __dynsym_load_start__ + SIZEOF(.dynsym);

  __dynstr_load_start__ =  ALIGN(__dynsym_end__ , 4);
  .dynstr ALIGN(__dynstr_load_start__ , 4) : AT(ALIGN(__dynstr_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynstr))
    KEEP (*(.dynstr*))
    . = ALIGN(4);
  }
  __dynstr_end__ = __dynstr_load_start__ + SIZEOF(.dynstr);

  __reldyn_load_start__ =  ALIGN(__dynstr_end__ , 4);
  .rel.dyn ALIGN(__reldyn_load_start__ , 4) : AT(ALIGN(__reldyn_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.dyn))
    KEEP (*(.rel.dyn*))
    . = ALIGN(4);
  }
  __reldyn_end__ = __reldyn_load_start__ + SIZEOF(.rel.dyn);

  __relplt_load_start__ =  ALIGN(__reldyn_end__ , 4);
  .rel.plt ALIGN(__relplt_load_start__ , 4) : AT(ALIGN(__relplt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.plt))
    KEEP (*(.rel.plt*))
    . = ALIGN(4);
  }
  __relplt_end__ = __relplt_load_start__ + SIZEOF(.rel.plt);

  __plt_load_start__ =  ALIGN(__relplt_end__ , 4);
  .plt ALIGN(__plt_load_start__ , 4) : AT(ALIGN(__plt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.plt))
    KEEP (*(.plt*))
    . = ALIGN(4);
  }
  __plt_end__ = __plt_load_start__ + SIZEOF(.plt);

  __interp_load_start__ =  ALIGN(__plt_end__ , 4);
  .interp ALIGN(__interp_load_start__ , 4) : AT(ALIGN(__interp_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.interp))
    KEEP (*(.interp*))
    . = ALIGN(4);
  }
  __interp_end__ = __interp_load_start__ + SIZEOF(.interp);

  __hash_load_start__ =  ALIGN(__interp_end__ , 4);
  .hash ALIGN(__hash_load_start__ , 4) : AT(ALIGN(__hash_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.hash))
    KEEP (*(.hash*))
    . = ALIGN(4);
  }
  __hash_end__ = __hash_load_start__ + SIZEOF(.hash);

  __text_load_start__ =  ALIGN(__hash_end__ , 4);
  .text ALIGN(__text_load_start__ , 4) : AT(ALIGN(__text_load_start__, 4))
  {
    __text_start__ = .;
    *(.text .text.* .glue_7t .glue_7 .gnu.linkonce.t.* .gcc_except_table  )
  }
  __text_end__ = __text_start__ + SIZEOF(.text);

  __dtors_load_start__ = ALIGN(__text_end__ , 4);
  .dtors ALIGN(__text_end__ , 4) : AT(ALIGN(__text_end__ , 4))
  {
    __dtors_start__ = .;
    KEEP (*(SORT(.dtors.*))) KEEP (*(.dtors))
  }
  __dtors_end__ = __dtors_start__ + SIZEOF(.dtors);

  __ctors_load_start__ = ALIGN(__dtors_end__ , 4);
  .ctors ALIGN(__dtors_end__ , 4) : AT(ALIGN(__dtors_end__ , 4))
  {
    __ctors_start__ = .;
    KEEP (*(SORT(.ctors.*))) KEEP (*(.ctors))
  }
  __ctors_end__ = __ctors_start__ + SIZEOF(.ctors);

  __got_load_start__ = ALIGN(__ctors_end__ , 4);
  .got ALIGN(__ctors_end__ , 4) : AT(ALIGN(__ctors_end__ , 4))
  {
    . = ALIGN(4);
    _sgot = .;
    KEEP (*(.got))
    KEEP (*(.got*))
    . = ALIGN(4);
    _egot = .;
  } 
  __got_end__ =  __got_load_start__ + SIZEOF(.got);

  __rodata_load_start__ = ALIGN(__got_end__ , 4);
  .rodata ALIGN(__got_end__ , 4) : AT(ALIGN(__got_end__ , 4))
  {
    __rodata_start__ = .;
    *(.rodata .rodata.* .gnu.linkonce.r.*)
  }
  __rodata_end__ = __rodata_start__ + SIZEOF(.rodata);
 
  __code_size__ =  __rodata_end__ - __FLASH_segment_start__;

  __fast_load_start__ = ALIGN(__rodata_end__ , 4);

  __fast_load_end__ = __fast_load_start__ + SIZEOF(.fast);

  __new_got_start__ = ALIGN(__RAM_segment_start__ , 4);

  __new_got_end__ =  __new_got_start__ + SIZEOF(.got);

  .fast ALIGN(__new_got_end__ , 4) : AT(ALIGN(__rodata_end__ , 4))
  {
    __fast_start__ = .;
    *(.fast .fast.*)
  }
  __fast_end__ = __fast_start__ + SIZEOF(.fast);

  .fast_run ALIGN(__fast_end__ , 4) (NOLOAD) :
  {
    __fast_run_start__ = .;
    . = MAX(__fast_run_start__ + SIZEOF(.fast), .);
  }
  __fast_run_end__ = __fast_run_start__ + SIZEOF(.fast_run);

  __data_load_start__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4);
  .data ALIGN(__fast_run_end__ , 4) : AT(ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4))
  {
    __data_start__ = .;
    *(.data .data.* .gnu.linkonce.d.*)
  }
  __data_end__ = __data_start__ + SIZEOF(.data);

  __data_load_end__ = __data_load_start__ + SIZEOF(.data);

  __FLASH_segment_used_end__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4) + SIZEOF(.data);

  .data_run ALIGN(__fast_run_end__ , 4) (NOLOAD) :
  {
    __data_run_start__ = .;
    . = MAX(__data_run_start__ + SIZEOF(.data), .);
  }
  __data_run_end__ = __data_run_start__ + SIZEOF(.data_run);

  __bss_load_start__ = ALIGN(__data_run_end__ , 4);
  .bss ALIGN(__data_run_end__ , 4) (NOLOAD) : AT(ALIGN(__data_run_end__ , 4))
  {
    __bss_start__ = .;
    *(.bss .bss.* .gnu.linkonce.b.*) *(COMMON)
  }
  __bss_end__ = __bss_start__ + SIZEOF(.bss);

  __non_init_load_start__ = ALIGN(__bss_end__ , 4);
  .non_init ALIGN(__bss_end__ , 4) (NOLOAD) : AT(ALIGN(__bss_end__ , 4))
  {
    __non_init_start__ = .;
    *(.non_init .non_init.*)
  }
  __non_init_end__ = __non_init_start__ + SIZEOF(.non_init);

  __heap_load_start__ = ALIGN(__non_init_end__ , 4);
  .heap ALIGN(__non_init_end__ , 4) (NOLOAD) : AT(ALIGN(__non_init_end__ , 4))
  {
    __heap_start__ = .;
    *(.heap)
    . = ALIGN(MAX(__heap_start__ + __HEAPSIZE__ , .), 4);
  }
  __heap_end__ = __heap_start__ + SIZEOF(.heap);

  __data_size__ =  __heap_end__ - __RAM_segment_start__;

}
```

#### <a name="building-modules-for-cortex-m4-using-gnu"></a><span data-ttu-id="11426-652">GNU를 사용하는 Cortex-M4의 모듈 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-652">Building Modules for Cortex-M4 using GNU</span></span>

<span data-ttu-id="11426-653">build_threadx_module_sample.bat를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="11426-653">See build_threadx_module_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base txm_module_preamble.s
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module.c
arm-none-eabi-ld -A cortex-m4 -T sample_threadx_module.ld txm_module_preamble.o gcc_setup.o sample_threadx_module.o -e _txm_module_thread_shell_entry txm.a -o sample_threadx_module.axf -M > sample_threadx_module.map
```

#### <a name="thread-extension-definition-for-cortex-m4-using-gnu"></a><span data-ttu-id="11426-654">GNU를 사용하는 Cortex-M4의 스레드 확장 정의</span><span class="sxs-lookup"><span data-stu-id="11426-654">Thread extension definition for Cortex-M4 using GNU</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m4-using-gnu"></a><span data-ttu-id="11426-655">GNU를 사용하는 Cortex-M4의 모듈 관리자 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-655">Building Module Manager for Cortex-M4 using GNU</span></span>

<span data-ttu-id="11426-656">build_threadx_module_manager_sample.bat를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="11426-656">See build_threadx_module_manager_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb cortexm_vectors.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb cortexm_crt0.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb tx_initialize_low_level.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module_manager.c
arm-none-eabi-gcc -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb -T sample_threadx.ld -ereset_handler -nostartfiles -o sample_threadx_module_manager.out -Wl,-Map=sample_threadx_module_manager.map cortexm_vectors.o cortexm_crt0.o tx_initialize_low_level.o sample_threadx_module_manager.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-gnu"></a><span data-ttu-id="11426-657">GNU를 사용하는 Cortex-M4의 외부 메모리 사용 API에 대한 특성</span><span class="sxs-lookup"><span data-stu-id="11426-657">Attributes for external memory enable API for Cortex-M4 using GNU</span></span>

<span data-ttu-id="11426-658">모듈에는 항상 공유 메모리에 대한 읽기 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-658">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="11426-659">특성 매개 변수</span><span class="sxs-lookup"><span data-stu-id="11426-659">Attribute parameter</span></span> | <span data-ttu-id="11426-660">의미</span><span class="sxs-lookup"><span data-stu-id="11426-660">Meaning</span></span> |
|---|---|
| <span data-ttu-id="11426-661">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="11426-661">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="11426-662">쓰기 액세스</span><span class="sxs-lookup"><span data-stu-id="11426-662">Write access</span></span> |

### <a name="cortex-m4-using-iar"></a><span data-ttu-id="11426-663">IAR을 사용하는 Cortex-M4</span><span class="sxs-lookup"><span data-stu-id="11426-663">Cortex-M4 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m4-using-iar"></a><span data-ttu-id="11426-664">IAR을 사용하는 Cortex-M4의 모듈 머리말</span><span class="sxs-lookup"><span data-stu-id="11426-664">Module preamble for Cortex-M4 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */

    PUBLIC __txm_module_preamble


    /* Define application-specific start/stop entry points for the module.  */

    EXTERN demo_module_start


    /* Define common external references.  */

    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        ; Module ID
    DC32      0x5                                               ; Module Major Version
    DC32      0x6                                               ; Module Minor Version
    DC32      32                                                ; Module Preamble Size in 32-bit words
    DC32      0x12345678                                        ; Module ID (application defined)
    DC32      0x00000007                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-3: Reserved
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution


    DC32      _txm_module_thread_shell_entry - . - 0            ; Module Shell Entry Point
    DC32      demo_module_start - . - 0                         ; Module Start Thread Entry Point
    DC32      0                                                 ; Module Stop Thread Entry Point
    DC32      1                                                 ; Module Start/Stop Thread Priority
    DC32      1024                                              ; Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 ; Module Callback Thread Entry
    DC32      1                                                 ; Module Callback Thread Priority
    DC32      1024                                              ; Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      ; Module Code Size
    DC32      RWPI$$Length                                      ; Module Data Size
    DC32      0                                                 ; Reserved 0
    DC32      0                                                 ; Reserved 1
    DC32      0                                                 ; Reserved 2
    DC32      0                                                 ; Reserved 3
    DC32      0                                                 ; Reserved 4
    DC32      0                                                 ; Reserved 5
    DC32      0                                                 ; Reserved 6
    DC32      0                                                 ; Reserved 7
    DC32      0                                                 ; Reserved 8  
    DC32      0                                                 ; Reserved 9
    DC32      0                                                 ; Reserved 10
    DC32      0                                                 ; Reserved 11
    DC32      0                                                 ; Reserved 12
    DC32      0                                                 ; Reserved 13
    DC32      0                                                 ; Reserved 14
    DC32      0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m4-using-iar"></a><span data-ttu-id="11426-665">IAR을 사용하는 Cortex-M4의 모듈 속성</span><span class="sxs-lookup"><span data-stu-id="11426-665">Module properties for Cortex-M4 using IAR</span></span>

| <span data-ttu-id="11426-666">bit</span><span class="sxs-lookup"><span data-stu-id="11426-666">Bit</span></span> | <span data-ttu-id="11426-667">값</span><span class="sxs-lookup"><span data-stu-id="11426-667">Value</span></span> | <span data-ttu-id="11426-668">의미</span><span class="sxs-lookup"><span data-stu-id="11426-668">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="11426-669">0</span><span class="sxs-lookup"><span data-stu-id="11426-669">0</span></span> | <span data-ttu-id="11426-670">0</span><span class="sxs-lookup"><span data-stu-id="11426-670">0</span></span><br /><span data-ttu-id="11426-671">1</span><span class="sxs-lookup"><span data-stu-id="11426-671">1</span></span> | <span data-ttu-id="11426-672">권한 있는 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-672">Privileged mode execution</span></span><br /><span data-ttu-id="11426-673">사용자 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-673">User mode execution</span></span> |
| <span data-ttu-id="11426-674">1</span><span class="sxs-lookup"><span data-stu-id="11426-674">1</span></span> | <span data-ttu-id="11426-675">0</span><span class="sxs-lookup"><span data-stu-id="11426-675">0</span></span><br /><span data-ttu-id="11426-676">1</span><span class="sxs-lookup"><span data-stu-id="11426-676">1</span></span> | <span data-ttu-id="11426-677">MPU 보호 없음</span><span class="sxs-lookup"><span data-stu-id="11426-677">No MPU protection</span></span><br /><span data-ttu-id="11426-678">MPU 보호(사용자 모드가 선택되어 있어야 함)</span><span class="sxs-lookup"><span data-stu-id="11426-678">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="11426-679">2</span><span class="sxs-lookup"><span data-stu-id="11426-679">2</span></span> | <span data-ttu-id="11426-680">0</span><span class="sxs-lookup"><span data-stu-id="11426-680">0</span></span><br /><span data-ttu-id="11426-681">1</span><span class="sxs-lookup"><span data-stu-id="11426-681">1</span></span> | <span data-ttu-id="11426-682">공유/외부 메모리 액세스 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="11426-682">Disable shared/external memory access</span></span><br /><span data-ttu-id="11426-683">공유/외부 메모리 액세스 사용</span><span class="sxs-lookup"><span data-stu-id="11426-683">Enable shared/external memory access</span></span> |
| <span data-ttu-id="11426-684">[23-3]</span><span class="sxs-lookup"><span data-stu-id="11426-684">[23-3]</span></span> | <span data-ttu-id="11426-685">0</span><span class="sxs-lookup"><span data-stu-id="11426-685">0</span></span> | <span data-ttu-id="11426-686">예약됨</span><span class="sxs-lookup"><span data-stu-id="11426-686">Reserved</span></span>
| <span data-ttu-id="11426-687">[31-24]</span><span class="sxs-lookup"><span data-stu-id="11426-687">[31-24]</span></span> | <br /><span data-ttu-id="11426-688">0x00</span><span class="sxs-lookup"><span data-stu-id="11426-688">0x00</span></span><br /><span data-ttu-id="11426-689">0x01</span><span class="sxs-lookup"><span data-stu-id="11426-689">0x01</span></span><br /><span data-ttu-id="11426-690">0x02</span><span class="sxs-lookup"><span data-stu-id="11426-690">0x02</span></span> | <span data-ttu-id="11426-691">**컴파일러 ID**</span><span class="sxs-lookup"><span data-stu-id="11426-691">**Compiler ID**</span></span><br /><span data-ttu-id="11426-692">IAR</span><span class="sxs-lookup"><span data-stu-id="11426-692">IAR</span></span><br /><span data-ttu-id="11426-693">ARM</span><span class="sxs-lookup"><span data-stu-id="11426-693">ARM</span></span><br /><span data-ttu-id="11426-694">GNU</span><span class="sxs-lookup"><span data-stu-id="11426-694">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-iar"></a><span data-ttu-id="11426-695">IAR을 사용하는 Cortex-M4의 모듈 링커</span><span class="sxs-lookup"><span data-stu-id="11426-695">Module linker for Cortex-M4 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\a_v1_0.xml" */
/*-Specials-*/
define symbol __ICFEDIT_intvec_start__ = 0x0;
/*-Memory Regions-*/
define symbol __ICFEDIT_region_ROM_start__ = 0x080f0000;
define symbol __ICFEDIT_region_ROM_end__   = 0x080fffff;
define symbol __ICFEDIT_region_RAM_start__ = 0x64002800;
define symbol __ICFEDIT_region_RAM_end__   = 0x64100000;
/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__   = 0;
define symbol __ICFEDIT_size_svcstack__ = 0;
define symbol __ICFEDIT_size_irqstack__ = 0;
define symbol __ICFEDIT_size_fiqstack__ = 0;
define symbol __ICFEDIT_size_undstack__ = 0;
define symbol __ICFEDIT_size_abtstack__ = 0;
define symbol __ICFEDIT_size_heap__     = 0x1000;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region ROM_region   = mem:[from __ICFEDIT_region_ROM_start__   to __ICFEDIT_region_ROM_end__];
define region RAM_region   = mem:[from __ICFEDIT_region_RAM_start__   to __ICFEDIT_region_RAM_end__];

//define block CSTACK    with alignment = 8, size = __ICFEDIT_size_cstack__   { };
//define block SVC_STACK with alignment = 8, size = __ICFEDIT_size_svcstack__ { };
//define block IRQ_STACK with alignment = 8, size = __ICFEDIT_size_irqstack__ { };
//define block FIQ_STACK with alignment = 8, size = __ICFEDIT_size_fiqstack__ { };
//define block UND_STACK with alignment = 8, size = __ICFEDIT_size_undstack__ { };
//define block ABT_STACK with alignment = 8, size = __ICFEDIT_size_abtstack__ { };
define block HEAP      with alignment = 8, size = __ICFEDIT_size_heap__     { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

//place at address mem:__ICFEDIT_intvec_start__ { readonly section .intvec };

define movable block ROPI with alignment = 4, fixed order
{
  ro object txm_module_preamble_stm32f4xx.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-m4-using-iar"></a><span data-ttu-id="11426-696">IAR을 사용하는 Cortex-M4의 모듈 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-696">Building Modules for Cortex-M4 using IAR</span></span>

<span data-ttu-id="11426-697">예제 작업 영역이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="11426-697">An example workspace is provided.</span></span> <span data-ttu-id="11426-698">ThreadX 라이브러리, ThreadX 모듈 라이브러리, 데모 모듈 프로젝트 및 데모 모듈 관리자 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="11426-698">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m4-using-iar"></a><span data-ttu-id="11426-699">IAR을 사용하는 Cortex-M4의 스레드 확장 정의</span><span class="sxs-lookup"><span data-stu-id="11426-699">Thread extension definition for Cortex-M4 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_saved_lr;              \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-m4-using-iar"></a><span data-ttu-id="11426-700">IAR을 사용하는 Cortex-M4의 모듈 관리자 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-700">Building Module Manager for Cortex-M4 using IAR</span></span>

<span data-ttu-id="11426-701">예제 작업 영역이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="11426-701">An example workspace is provided.</span></span> <span data-ttu-id="11426-702">ThreadX 라이브러리, ThreadX 모듈 라이브러리, 데모 모듈 프로젝트 및 데모 모듈 관리자 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="11426-702">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-iar"></a><span data-ttu-id="11426-703">IAR을 사용하는 Cortex-M4의 외부 메모리 사용 API에 대한 특성</span><span class="sxs-lookup"><span data-stu-id="11426-703">Attributes for external memory enable API for Cortex-M4 using IAR</span></span>

<span data-ttu-id="11426-704">모듈에는 항상 공유 메모리에 대한 읽기 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-704">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="11426-705">특성 매개 변수</span><span class="sxs-lookup"><span data-stu-id="11426-705">Attribute parameter</span></span> | <span data-ttu-id="11426-706">의미</span><span class="sxs-lookup"><span data-stu-id="11426-706">Meaning</span></span> |
|---|---|
| <span data-ttu-id="11426-707">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="11426-707">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="11426-708">쓰기 액세스</span><span class="sxs-lookup"><span data-stu-id="11426-708">Write access</span></span> |

## <a name="cortex-m7-processor"></a><span data-ttu-id="11426-709">Cortex-M7 프로세서</span><span class="sxs-lookup"><span data-stu-id="11426-709">Cortex-M7 processor</span></span>

### <a name="cortex-m7-using-ac5"></a><span data-ttu-id="11426-710">AC5를 사용하는 Cortex-M7</span><span class="sxs-lookup"><span data-stu-id="11426-710">Cortex-M7 using AC5</span></span>

#### <a name="module-preamble-for-cortex-m7-using-ac5"></a><span data-ttu-id="11426-711">AC5를 사용하는 Cortex-M7의 모듈 머리말</span><span class="sxs-lookup"><span data-stu-id="11426-711">Module preamble for Cortex-M7 using AC5</span></span>

```c
    AREA Init, CODE, READONLY

    PRESERVE8

    ; Define public symbols

    EXPORT __txm_module_preamble


    ; Define application-specific start/stop entry points for the module

    EXTERN demo_module_start


    ; Define common external references

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|
    IMPORT  |Image$$ER_RW$$Length|
    IMPORT  |Image$$ER_RW$$RW$$Length|
    IMPORT  |Image$$ER_RW$$ZI$$Length|
    IMPORT  |Image$$ER_ZI$$ZI$$Length|

__txm_module_preamble
    DCD     0x4D4F4455                                          ; Module ID
    DCD     0x5                                                 ; Module Major Version
    DCD     0x6                                                 ; Module Minor Version
    DCD     32                                                  ; Module Preamble Size in 32-bit words
    DCD     0x12345678                                          ; Module ID (application defined)
    DCD     0x01000007                                          ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected)
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
    DCD     _txm_module_thread_shell_entry - __txm_module_preamble              ; Module Shell Entry Point
    DCD     demo_module_start - __txm_module_preamble           ; Module Start Thread Entry Point
    DCD     0                                                   ; Module Stop Thread Entry Point
    DCD     1                                                   ; Module Start/Stop Thread Priority
    DCD     1024                                                ; Module Start/Stop Thread Stack Size
    DCD     _txm_module_callback_request_thread_entry - __txm_module_preamble   ; Module Callback Thread Entry
    DCD     1                                                   ; Module Callback Thread Priority
    DCD     1024                                                ; Module Callback Thread Stack Size
    DCD     |Image$$ER_RO$$Length| + |Image$$ER_RW$$Length|         ; Module Code Size
    DCD     |Image$$ER_RW$$Length| + |Image$$ER_ZI$$ZI$$Length| ; Module Data Size
    DCD     0                                                   ; Reserved 0
    DCD     0                                                   ; Reserved 1
    DCD     0                                                   ; Reserved 2
    DCD     0                                                   ; Reserved 3
    DCD     0                                                   ; Reserved 4
    DCD     0                                                   ; Reserved 5
    DCD     0                                                   ; Reserved 6
    DCD     0                                                   ; Reserved 7
    DCD     0                                                   ; Reserved 8
    DCD     0                                                   ; Reserved 9
    DCD     0                                                   ; Reserved 10
    DCD     0                                                   ; Reserved 11
    DCD     0                                                   ; Reserved 12
    DCD     0                                                   ; Reserved 13
    DCD     0                                                   ; Reserved 14
    DCD     0                                                   ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m7-using-ac5"></a><span data-ttu-id="11426-712">AC5를 사용하는 Cortex-M7의 모듈 속성</span><span class="sxs-lookup"><span data-stu-id="11426-712">Module properties for Cortex-M7 using AC5</span></span>

| <span data-ttu-id="11426-713">bit</span><span class="sxs-lookup"><span data-stu-id="11426-713">Bit</span></span> | <span data-ttu-id="11426-714">값</span><span class="sxs-lookup"><span data-stu-id="11426-714">Value</span></span> | <span data-ttu-id="11426-715">의미</span><span class="sxs-lookup"><span data-stu-id="11426-715">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="11426-716">0</span><span class="sxs-lookup"><span data-stu-id="11426-716">0</span></span> | <span data-ttu-id="11426-717">0</span><span class="sxs-lookup"><span data-stu-id="11426-717">0</span></span><br /><span data-ttu-id="11426-718">1</span><span class="sxs-lookup"><span data-stu-id="11426-718">1</span></span> | <span data-ttu-id="11426-719">권한 있는 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-719">Privileged mode execution</span></span><br /><span data-ttu-id="11426-720">사용자 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-720">User mode execution</span></span> |
| <span data-ttu-id="11426-721">1</span><span class="sxs-lookup"><span data-stu-id="11426-721">1</span></span> | <span data-ttu-id="11426-722">0</span><span class="sxs-lookup"><span data-stu-id="11426-722">0</span></span><br /><span data-ttu-id="11426-723">1</span><span class="sxs-lookup"><span data-stu-id="11426-723">1</span></span> | <span data-ttu-id="11426-724">MPU 보호 없음</span><span class="sxs-lookup"><span data-stu-id="11426-724">No MPU protection</span></span><br /><span data-ttu-id="11426-725">MPU 보호(사용자 모드가 선택되어 있어야 함)</span><span class="sxs-lookup"><span data-stu-id="11426-725">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="11426-726">2</span><span class="sxs-lookup"><span data-stu-id="11426-726">2</span></span> | <span data-ttu-id="11426-727">0</span><span class="sxs-lookup"><span data-stu-id="11426-727">0</span></span><br /><span data-ttu-id="11426-728">1</span><span class="sxs-lookup"><span data-stu-id="11426-728">1</span></span> | <span data-ttu-id="11426-729">공유/외부 메모리 액세스 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="11426-729">Disable shared/external memory access</span></span><br /><span data-ttu-id="11426-730">공유/외부 메모리 액세스 사용</span><span class="sxs-lookup"><span data-stu-id="11426-730">Enable shared/external memory access</span></span> |
| <span data-ttu-id="11426-731">[23-3]</span><span class="sxs-lookup"><span data-stu-id="11426-731">[23-3]</span></span> | <span data-ttu-id="11426-732">0</span><span class="sxs-lookup"><span data-stu-id="11426-732">0</span></span> | <span data-ttu-id="11426-733">예약됨</span><span class="sxs-lookup"><span data-stu-id="11426-733">Reserved</span></span>
| <span data-ttu-id="11426-734">[31-24]</span><span class="sxs-lookup"><span data-stu-id="11426-734">[31-24]</span></span> | <br /><span data-ttu-id="11426-735">0x00</span><span class="sxs-lookup"><span data-stu-id="11426-735">0x00</span></span><br /><span data-ttu-id="11426-736">0x01</span><span class="sxs-lookup"><span data-stu-id="11426-736">0x01</span></span><br /><span data-ttu-id="11426-737">0x02</span><span class="sxs-lookup"><span data-stu-id="11426-737">0x02</span></span> | <span data-ttu-id="11426-738">**컴파일러 ID**</span><span class="sxs-lookup"><span data-stu-id="11426-738">**Compiler ID**</span></span><br /><span data-ttu-id="11426-739">IAR</span><span class="sxs-lookup"><span data-stu-id="11426-739">IAR</span></span><br /><span data-ttu-id="11426-740">ARM</span><span class="sxs-lookup"><span data-stu-id="11426-740">ARM</span></span><br /><span data-ttu-id="11426-741">GNU</span><span class="sxs-lookup"><span data-stu-id="11426-741">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-ac5"></a><span data-ttu-id="11426-742">AC5를 사용하는 Cortex-M7의 모듈 링커</span><span class="sxs-lookup"><span data-stu-id="11426-742">Module linker for Cortex-M7 using AC5</span></span>

<span data-ttu-id="11426-743">명령줄을 기반으로 하며 링커 파일 예제는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-743">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-cortex-m7-using-ac5"></a><span data-ttu-id="11426-744">AC5를 사용하는 Cortex-M7의 모듈 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-744">Building Modules for Cortex-M7 using AC5</span></span>

<span data-ttu-id="11426-745">AC5를 사용하여 Cortex-M7 모듈을 빌드하는 간단한 명령줄 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-745">A simple command-line example for building a Cortex-M7 module using AC5:</span></span>

```dos
armasm -g --cpu=cortex-m7 --fpu=softvfp --apcs=/interwork/ropi/rwpi txm_module_preamble.s
armcc  -g --cpu=cortex-m7 --fpu=softvfp -c --apcs=/interwork/ropi/rwpi --lower_ropi -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module.c
armlink -d -o sample_threadx_module.axf --elf --ro 0 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list sample_threadx_module.map txm_module_preamble.o sample_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-m7-using-ac5"></a><span data-ttu-id="11426-746">AC5를 사용하는 Cortex-M7의 스레드 확장 정의</span><span class="sxs-lookup"><span data-stu-id="11426-746">Thread extension definition for Cortex-M7 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_saved_lr;              \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m7-using-ac5"></a><span data-ttu-id="11426-747">AC5를 사용하는 Cortex-M7의 모듈 관리자 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-747">Building Module Manager for Cortex-M7 using AC5</span></span>

<span data-ttu-id="11426-748">AC5를 사용하여 Cortex-M7 모듈 관리자를 빌드하는 간단한 명령줄 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-748">A simple command-line example for building a Cortex-M7 module manager using AC5:</span></span>

```dos
armasm -g --cpu=cortex-m7 --fpu=softvfp --apcs=interwork tx_initialize_low_level.s
armcc -g --cpu=cortex-m7 --fpu=softvfp -c demo_threadx_module_manager.c
armcc -g --cpu=cortex-m7 --fpu=softvfp -c module_code.c
armlink -d -o demo_threadx_module_manager.axf --elf --ro 0x00000000 --first tx_initialize_low_level.o(RESET) --remove --map --symbols --list demo_threadx_module_manager.map tx_initialize_low_level.o demo_threadx_module_manager.o module_code.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-ac5"></a><span data-ttu-id="11426-749">AC5를 사용하는 Cortex-M7의 외부 메모리 사용 API에 대한 특성</span><span class="sxs-lookup"><span data-stu-id="11426-749">Attributes for external memory enable API for Cortex-M7 using AC5</span></span>

### <a name="cortex-m7-using-ac6"></a><span data-ttu-id="11426-750">AC6을 사용하는 Cortex-M7</span><span class="sxs-lookup"><span data-stu-id="11426-750">Cortex-M7 using AC6</span></span>

#### <a name="module-properties-for-cortex-m7-using-ac6"></a><span data-ttu-id="11426-751">AC6을 사용하는 Cortex-M7의 모듈 속성</span><span class="sxs-lookup"><span data-stu-id="11426-751">Module properties for Cortex-M7 using AC6</span></span>

| <span data-ttu-id="11426-752">bit</span><span class="sxs-lookup"><span data-stu-id="11426-752">Bit</span></span> | <span data-ttu-id="11426-753">값</span><span class="sxs-lookup"><span data-stu-id="11426-753">Value</span></span> | <span data-ttu-id="11426-754">의미</span><span class="sxs-lookup"><span data-stu-id="11426-754">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="11426-755">0</span><span class="sxs-lookup"><span data-stu-id="11426-755">0</span></span> | <span data-ttu-id="11426-756">0</span><span class="sxs-lookup"><span data-stu-id="11426-756">0</span></span><br /><span data-ttu-id="11426-757">1</span><span class="sxs-lookup"><span data-stu-id="11426-757">1</span></span> | <span data-ttu-id="11426-758">권한 있는 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-758">Privileged mode execution</span></span><br /><span data-ttu-id="11426-759">사용자 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-759">User mode execution</span></span> |
| <span data-ttu-id="11426-760">1</span><span class="sxs-lookup"><span data-stu-id="11426-760">1</span></span> | <span data-ttu-id="11426-761">0</span><span class="sxs-lookup"><span data-stu-id="11426-761">0</span></span><br /><span data-ttu-id="11426-762">1</span><span class="sxs-lookup"><span data-stu-id="11426-762">1</span></span> | <span data-ttu-id="11426-763">MPU 보호 없음</span><span class="sxs-lookup"><span data-stu-id="11426-763">No MPU protection</span></span><br /><span data-ttu-id="11426-764">MPU 보호(사용자 모드가 선택되어 있어야 함)</span><span class="sxs-lookup"><span data-stu-id="11426-764">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="11426-765">2</span><span class="sxs-lookup"><span data-stu-id="11426-765">2</span></span> | <span data-ttu-id="11426-766">0</span><span class="sxs-lookup"><span data-stu-id="11426-766">0</span></span><br /><span data-ttu-id="11426-767">1</span><span class="sxs-lookup"><span data-stu-id="11426-767">1</span></span> | <span data-ttu-id="11426-768">공유/외부 메모리 액세스 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="11426-768">Disable shared/external memory access</span></span><br /><span data-ttu-id="11426-769">공유/외부 메모리 액세스 사용</span><span class="sxs-lookup"><span data-stu-id="11426-769">Enable shared/external memory access</span></span> |
| <span data-ttu-id="11426-770">[23-3]</span><span class="sxs-lookup"><span data-stu-id="11426-770">[23-3]</span></span> | <span data-ttu-id="11426-771">0</span><span class="sxs-lookup"><span data-stu-id="11426-771">0</span></span> | <span data-ttu-id="11426-772">예약됨</span><span class="sxs-lookup"><span data-stu-id="11426-772">Reserved</span></span>
| <span data-ttu-id="11426-773">[31-24]</span><span class="sxs-lookup"><span data-stu-id="11426-773">[31-24]</span></span> | <br /><span data-ttu-id="11426-774">0x00</span><span class="sxs-lookup"><span data-stu-id="11426-774">0x00</span></span><br /><span data-ttu-id="11426-775">0x01</span><span class="sxs-lookup"><span data-stu-id="11426-775">0x01</span></span><br /><span data-ttu-id="11426-776">0x02</span><span class="sxs-lookup"><span data-stu-id="11426-776">0x02</span></span> | <span data-ttu-id="11426-777">**컴파일러 ID**</span><span class="sxs-lookup"><span data-stu-id="11426-777">**Compiler ID**</span></span><br /><span data-ttu-id="11426-778">IAR</span><span class="sxs-lookup"><span data-stu-id="11426-778">IAR</span></span><br /><span data-ttu-id="11426-779">ARM</span><span class="sxs-lookup"><span data-stu-id="11426-779">ARM</span></span><br /><span data-ttu-id="11426-780">GNU</span><span class="sxs-lookup"><span data-stu-id="11426-780">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-ac6"></a><span data-ttu-id="11426-781">AC6을 사용하는 Cortex-M7의 모듈 링커</span><span class="sxs-lookup"><span data-stu-id="11426-781">Module linker for Cortex-M7 using AC6</span></span>

<span data-ttu-id="11426-782">링커 파일이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-782">No linker file is used.</span></span> <span data-ttu-id="11426-783">프로젝트 설정을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="11426-783">See project settings.</span></span>

#### <a name="building-modules-for-cortex-m7-using-ac6"></a><span data-ttu-id="11426-784">AC6을 사용하는 Cortex-M7의 모듈 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-784">Building Modules for Cortex-M7 using AC6</span></span>

<span data-ttu-id="11426-785">예제 작업 영역이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="11426-785">An example workspace is provided.</span></span> <span data-ttu-id="11426-786">ThreadX 라이브러리, ThreadX 모듈 라이브러리, 샘플 모듈 프로젝트 및 샘플 모듈 관리자 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="11426-786">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m7-using-ac6"></a><span data-ttu-id="11426-787">AC6을 사용하는 Cortex-M7의 스레드 확장 정의</span><span class="sxs-lookup"><span data-stu-id="11426-787">Thread extension definition for Cortex-M7 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m7-using-ac6"></a><span data-ttu-id="11426-788">AC6을 사용하는 Cortex-M7의 모듈 관리자 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-788">Building Module Manager for Cortex-M7 using AC6</span></span>

<span data-ttu-id="11426-789">예제 작업 영역이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="11426-789">An example workspace is provided.</span></span> <span data-ttu-id="11426-790">ThreadX 라이브러리, ThreadX 모듈 라이브러리, 샘플 모듈 프로젝트 및 샘플 모듈 관리자 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="11426-790">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-ac6"></a><span data-ttu-id="11426-791">AC6을 사용하는 Cortex-M7의 외부 메모리 사용 API에 대한 특성</span><span class="sxs-lookup"><span data-stu-id="11426-791">Attributes for external memory enable API for Cortex-M7 using AC6</span></span>

<span data-ttu-id="11426-792">모듈에는 항상 공유 메모리에 대한 읽기 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-792">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="11426-793">특성 매개 변수</span><span class="sxs-lookup"><span data-stu-id="11426-793">Attribute parameter</span></span> | <span data-ttu-id="11426-794">의미</span><span class="sxs-lookup"><span data-stu-id="11426-794">Meaning</span></span> |
|---|---|
| <span data-ttu-id="11426-795">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="11426-795">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="11426-796">쓰기 액세스</span><span class="sxs-lookup"><span data-stu-id="11426-796">Write access</span></span> |

### <a name="cortex-m7-using-gnu"></a><span data-ttu-id="11426-797">GNU를 사용하는 Cortex-M7</span><span class="sxs-lookup"><span data-stu-id="11426-797">Cortex-M7 using GNU</span></span>

#### <a name="module-properties-for-cortex-m7-using-gnu"></a><span data-ttu-id="11426-798">GNU를 사용하는 Cortex-M7의 모듈 속성</span><span class="sxs-lookup"><span data-stu-id="11426-798">Module properties for Cortex-M7 using GNU</span></span>

| <span data-ttu-id="11426-799">bit</span><span class="sxs-lookup"><span data-stu-id="11426-799">Bit</span></span> | <span data-ttu-id="11426-800">값</span><span class="sxs-lookup"><span data-stu-id="11426-800">Value</span></span> | <span data-ttu-id="11426-801">의미</span><span class="sxs-lookup"><span data-stu-id="11426-801">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="11426-802">0</span><span class="sxs-lookup"><span data-stu-id="11426-802">0</span></span> | <span data-ttu-id="11426-803">0</span><span class="sxs-lookup"><span data-stu-id="11426-803">0</span></span><br /><span data-ttu-id="11426-804">1</span><span class="sxs-lookup"><span data-stu-id="11426-804">1</span></span> | <span data-ttu-id="11426-805">권한 있는 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-805">Privileged mode execution</span></span><br /><span data-ttu-id="11426-806">사용자 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-806">User mode execution</span></span> |
| <span data-ttu-id="11426-807">1</span><span class="sxs-lookup"><span data-stu-id="11426-807">1</span></span> | <span data-ttu-id="11426-808">0</span><span class="sxs-lookup"><span data-stu-id="11426-808">0</span></span><br /><span data-ttu-id="11426-809">1</span><span class="sxs-lookup"><span data-stu-id="11426-809">1</span></span> | <span data-ttu-id="11426-810">MPU 보호 없음</span><span class="sxs-lookup"><span data-stu-id="11426-810">No MPU protection</span></span><br /><span data-ttu-id="11426-811">MPU 보호(사용자 모드가 선택되어 있어야 함)</span><span class="sxs-lookup"><span data-stu-id="11426-811">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="11426-812">2</span><span class="sxs-lookup"><span data-stu-id="11426-812">2</span></span> | <span data-ttu-id="11426-813">0</span><span class="sxs-lookup"><span data-stu-id="11426-813">0</span></span><br /><span data-ttu-id="11426-814">1</span><span class="sxs-lookup"><span data-stu-id="11426-814">1</span></span> | <span data-ttu-id="11426-815">공유/외부 메모리 액세스 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="11426-815">Disable shared/external memory access</span></span><br /><span data-ttu-id="11426-816">공유/외부 메모리 액세스 사용</span><span class="sxs-lookup"><span data-stu-id="11426-816">Enable shared/external memory access</span></span> |
| <span data-ttu-id="11426-817">[23-3]</span><span class="sxs-lookup"><span data-stu-id="11426-817">[23-3]</span></span> | <span data-ttu-id="11426-818">0</span><span class="sxs-lookup"><span data-stu-id="11426-818">0</span></span> | <span data-ttu-id="11426-819">예약됨</span><span class="sxs-lookup"><span data-stu-id="11426-819">Reserved</span></span>
| <span data-ttu-id="11426-820">[31-24]</span><span class="sxs-lookup"><span data-stu-id="11426-820">[31-24]</span></span> | <br /><span data-ttu-id="11426-821">0x00</span><span class="sxs-lookup"><span data-stu-id="11426-821">0x00</span></span><br /><span data-ttu-id="11426-822">0x01</span><span class="sxs-lookup"><span data-stu-id="11426-822">0x01</span></span><br /><span data-ttu-id="11426-823">0x02</span><span class="sxs-lookup"><span data-stu-id="11426-823">0x02</span></span> | <span data-ttu-id="11426-824">**컴파일러 ID**</span><span class="sxs-lookup"><span data-stu-id="11426-824">**Compiler ID**</span></span><br /><span data-ttu-id="11426-825">IAR</span><span class="sxs-lookup"><span data-stu-id="11426-825">IAR</span></span><br /><span data-ttu-id="11426-826">ARM</span><span class="sxs-lookup"><span data-stu-id="11426-826">ARM</span></span><br /><span data-ttu-id="11426-827">GNU</span><span class="sxs-lookup"><span data-stu-id="11426-827">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-gnu"></a><span data-ttu-id="11426-828">GNU를 사용하는 Cortex-M7의 모듈 링커</span><span class="sxs-lookup"><span data-stu-id="11426-828">Module linker for Cortex-M7 using GNU</span></span>

```c
MEMORY
{
  FLASH (rx) : ORIGIN = 0x00030000, LENGTH = 0x00010000
  RAM   (wx) : ORIGIN = 0, LENGTH = 0x00100000
}


SECTIONS
{
  __FLASH_segment_start__ = 0x00030000;
  __FLASH_segment_end__   = 0x00040000;
  __RAM_segment_start__   = 0;
  __RAM_segment_end__     = 0x8000;

  __HEAPSIZE__ = 128;

  __preamble_load_start__ = __FLASH_segment_start__;
  .preamble __FLASH_segment_start__ : AT(__FLASH_segment_start__)
  {
    __preamble_start__ = .;
    *(.preamble .preamble.*)
  }
  __preamble_end__ = __preamble_start__ + SIZEOF(.preamble);

  __dynsym_load_start__ =  ALIGN(__preamble_end__ , 4);
  .dynsym ALIGN(__dynsym_load_start__ , 4) : AT(ALIGN(__dynsym_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynsym))
    KEEP (*(.dynsym*))
    . = ALIGN(4);
  }
  __dynsym_end__ = __dynsym_load_start__ + SIZEOF(.dynsym);

  __dynstr_load_start__ =  ALIGN(__dynsym_end__ , 4);
  .dynstr ALIGN(__dynstr_load_start__ , 4) : AT(ALIGN(__dynstr_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynstr))
    KEEP (*(.dynstr*))
    . = ALIGN(4);
  }
  __dynstr_end__ = __dynstr_load_start__ + SIZEOF(.dynstr);

  __reldyn_load_start__ =  ALIGN(__dynstr_end__ , 4);
  .rel.dyn ALIGN(__reldyn_load_start__ , 4) : AT(ALIGN(__reldyn_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.dyn))
    KEEP (*(.rel.dyn*))
    . = ALIGN(4);
  }
  __reldyn_end__ = __reldyn_load_start__ + SIZEOF(.rel.dyn);

  __relplt_load_start__ =  ALIGN(__reldyn_end__ , 4);
  .rel.plt ALIGN(__relplt_load_start__ , 4) : AT(ALIGN(__relplt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.plt))
    KEEP (*(.rel.plt*))
    . = ALIGN(4);
  }
  __relplt_end__ = __relplt_load_start__ + SIZEOF(.rel.plt);

  __plt_load_start__ =  ALIGN(__relplt_end__ , 4);
  .plt ALIGN(__plt_load_start__ , 4) : AT(ALIGN(__plt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.plt))
    KEEP (*(.plt*))
    . = ALIGN(4);
  }
  __plt_end__ = __plt_load_start__ + SIZEOF(.plt);

  __interp_load_start__ =  ALIGN(__plt_end__ , 4);
  .interp ALIGN(__interp_load_start__ , 4) : AT(ALIGN(__interp_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.interp))
    KEEP (*(.interp*))
    . = ALIGN(4);
  }
  __interp_end__ = __interp_load_start__ + SIZEOF(.interp);

  __hash_load_start__ =  ALIGN(__interp_end__ , 4);
  .hash ALIGN(__hash_load_start__ , 4) : AT(ALIGN(__hash_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.hash))
    KEEP (*(.hash*))
    . = ALIGN(4);
  }
  __hash_end__ = __hash_load_start__ + SIZEOF(.hash);

  __text_load_start__ =  ALIGN(__hash_end__ , 4);
  .text ALIGN(__text_load_start__ , 4) : AT(ALIGN(__text_load_start__, 4))
  {
    __text_start__ = .;
    *(.text .text.* .glue_7t .glue_7 .gnu.linkonce.t.* .gcc_except_table  )
  }
  __text_end__ = __text_start__ + SIZEOF(.text);

  __dtors_load_start__ = ALIGN(__text_end__ , 4);
  .dtors ALIGN(__text_end__ , 4) : AT(ALIGN(__text_end__ , 4))
  {
    __dtors_start__ = .;
    KEEP (*(SORT(.dtors.*))) KEEP (*(.dtors))
  }
  __dtors_end__ = __dtors_start__ + SIZEOF(.dtors);

  __ctors_load_start__ = ALIGN(__dtors_end__ , 4);
  .ctors ALIGN(__dtors_end__ , 4) : AT(ALIGN(__dtors_end__ , 4))
  {
    __ctors_start__ = .;
    KEEP (*(SORT(.ctors.*))) KEEP (*(.ctors))
  }
  __ctors_end__ = __ctors_start__ + SIZEOF(.ctors);

  __got_load_start__ = ALIGN(__ctors_end__ , 4);
  .got ALIGN(__ctors_end__ , 4) : AT(ALIGN(__ctors_end__ , 4))
  {
    . = ALIGN(4);
    _sgot = .;
    KEEP (*(.got))
    KEEP (*(.got*))
    . = ALIGN(4);
    _egot = .;
  } 
  __got_end__ =  __got_load_start__ + SIZEOF(.got);

  __rodata_load_start__ = ALIGN(__got_end__ , 4);
  .rodata ALIGN(__got_end__ , 4) : AT(ALIGN(__got_end__ , 4))
  {
    __rodata_start__ = .;
    *(.rodata .rodata.* .gnu.linkonce.r.*)
  }
  __rodata_end__ = __rodata_start__ + SIZEOF(.rodata);
 
  __code_size__ =  __rodata_end__ - __FLASH_segment_start__;

  __fast_load_start__ = ALIGN(__rodata_end__ , 4);

  __fast_load_end__ = __fast_load_start__ + SIZEOF(.fast);

  __new_got_start__ = ALIGN(__RAM_segment_start__ , 4);

  __new_got_end__ =  __new_got_start__ + SIZEOF(.got);

  .fast ALIGN(__new_got_end__ , 4) : AT(ALIGN(__rodata_end__ , 4))
  {
    __fast_start__ = .;
    *(.fast .fast.*)
  }
  __fast_end__ = __fast_start__ + SIZEOF(.fast);

  .fast_run ALIGN(__fast_end__ , 4) (NOLOAD) :
  {
    __fast_run_start__ = .;
    . = MAX(__fast_run_start__ + SIZEOF(.fast), .);
  }
  __fast_run_end__ = __fast_run_start__ + SIZEOF(.fast_run);

  __data_load_start__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4);
  .data ALIGN(__fast_run_end__ , 4) : AT(ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4))
  {
    __data_start__ = .;
    *(.data .data.* .gnu.linkonce.d.*)
  }
  __data_end__ = __data_start__ + SIZEOF(.data);

  __data_load_end__ = __data_load_start__ + SIZEOF(.data);

  __FLASH_segment_used_end__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4) + SIZEOF(.data);

  .data_run ALIGN(__fast_run_end__ , 4) (NOLOAD) :
  {
    __data_run_start__ = .;
    . = MAX(__data_run_start__ + SIZEOF(.data), .);
  }
  __data_run_end__ = __data_run_start__ + SIZEOF(.data_run);

  __bss_load_start__ = ALIGN(__data_run_end__ , 4);
  .bss ALIGN(__data_run_end__ , 4) (NOLOAD) : AT(ALIGN(__data_run_end__ , 4))
  {
    __bss_start__ = .;
    *(.bss .bss.* .gnu.linkonce.b.*) *(COMMON)
  }
  __bss_end__ = __bss_start__ + SIZEOF(.bss);

  __non_init_load_start__ = ALIGN(__bss_end__ , 4);
  .non_init ALIGN(__bss_end__ , 4) (NOLOAD) : AT(ALIGN(__bss_end__ , 4))
  {
    __non_init_start__ = .;
    *(.non_init .non_init.*)
  }
  __non_init_end__ = __non_init_start__ + SIZEOF(.non_init);

  __heap_load_start__ = ALIGN(__non_init_end__ , 4);
  .heap ALIGN(__non_init_end__ , 4) (NOLOAD) : AT(ALIGN(__non_init_end__ , 4))
  {
    __heap_start__ = .;
    *(.heap)
    . = ALIGN(MAX(__heap_start__ + __HEAPSIZE__ , .), 4);
  }
  __heap_end__ = __heap_start__ + SIZEOF(.heap);

  __data_size__ =  __heap_end__ - __RAM_segment_start__;

}
```

#### <a name="building-modules-for-cortex-m7-using-gnu"></a><span data-ttu-id="11426-829">GNU를 사용하는 Cortex-M7의 모듈 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-829">Building Modules for Cortex-M7 using GNU</span></span>

<span data-ttu-id="11426-830">build_threadx_module_sample.bat를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="11426-830">See build_threadx_module_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base txm_module_preamble.s
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module.c
arm-none-eabi-ld -A cortex-m7 -T sample_threadx_module.ld txm_module_preamble.o gcc_setup.o sample_threadx_module.o -e _txm_module_thread_shell_entry txm.a -o sample_threadx_module.axf -M > sample_threadx_module.map
```

#### <a name="thread-extension-definition-for-cortex-m7-using-gnu"></a><span data-ttu-id="11426-831">GNU를 사용하는 Cortex-M7의 스레드 확장 정의</span><span class="sxs-lookup"><span data-stu-id="11426-831">Thread extension definition for Cortex-M7 using GNU</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m7-using-gnu"></a><span data-ttu-id="11426-832">GNU를 사용하는 Cortex-M7의 모듈 관리자 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-832">Building Module Manager for Cortex-M7 using GNU</span></span>

<span data-ttu-id="11426-833">build_threadx_module_manager_sample.bat를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="11426-833">See build_threadx_module_manager_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module_manager.c
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb tx_simulator_startup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb cortexm_crt0.S
arm-none-eabi-gcc -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb -nostartfiles -ereset_handler -T sample_threadx.ld tx_simulator_startup.o cortexm_crt0.o sample_threadx_module_manager.o tx.a -o sample_threadx_module_manager.axf -Wl,-Map=sample_threadx_module_manager.map
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-gnu"></a><span data-ttu-id="11426-834">GNU를 사용하는 Cortex-M7의 외부 메모리 사용 API에 대한 특성</span><span class="sxs-lookup"><span data-stu-id="11426-834">Attributes for external memory enable API for Cortex-M7 using GNU</span></span>

<span data-ttu-id="11426-835">모듈에는 항상 공유 메모리에 대한 읽기 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-835">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="11426-836">특성 매개 변수</span><span class="sxs-lookup"><span data-stu-id="11426-836">Attribute parameter</span></span> | <span data-ttu-id="11426-837">의미</span><span class="sxs-lookup"><span data-stu-id="11426-837">Meaning</span></span> |
|---|---|
| <span data-ttu-id="11426-838">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="11426-838">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="11426-839">쓰기 액세스</span><span class="sxs-lookup"><span data-stu-id="11426-839">Write access</span></span> |

### <a name="cortex-m7-using-iar"></a><span data-ttu-id="11426-840">IAR을 사용하는 Cortex-M7</span><span class="sxs-lookup"><span data-stu-id="11426-840">Cortex-M7 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m7-using-iar"></a><span data-ttu-id="11426-841">IAR을 사용하는 Cortex-M7의 모듈 머리말</span><span class="sxs-lookup"><span data-stu-id="11426-841">Module preamble for Cortex-M7 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */

    PUBLIC __txm_module_preamble


    /* Define application-specific start/stop entry points for the module.  */

    EXTERN demo_module_start


    /* Define common external references.  */

    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        ; Module ID
    DC32      0x5                                               ; Module Major Version
    DC32      0x6                                               ; Module Minor Version
    DC32      32                                                ; Module Preamble Size in 32-bit words
    DC32      0x12345678                                        ; Module ID (application defined)
    DC32      0x00000007                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-3: Reserved
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution


    DC32      _txm_module_thread_shell_entry - . - 0            ; Module Shell Entry Point
    DC32      demo_module_start - . - 0                         ; Module Start Thread Entry Point
    DC32      0                                                 ; Module Stop Thread Entry Point
    DC32      1                                                 ; Module Start/Stop Thread Priority
    DC32      1024                                              ; Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 ; Module Callback Thread Entry
    DC32      1                                                 ; Module Callback Thread Priority
    DC32      1024                                              ; Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      ; Module Code Size
    DC32      RWPI$$Length                                      ; Module Data Size
    DC32      0                                                 ; Reserved 0
    DC32      0                                                 ; Reserved 1
    DC32      0                                                 ; Reserved 2
    DC32      0                                                 ; Reserved 3
    DC32      0                                                 ; Reserved 4
    DC32      0                                                 ; Reserved 5
    DC32      0                                                 ; Reserved 6
    DC32      0                                                 ; Reserved 7
    DC32      0                                                 ; Reserved 8  
    DC32      0                                                 ; Reserved 9
    DC32      0                                                 ; Reserved 10
    DC32      0                                                 ; Reserved 11
    DC32      0                                                 ; Reserved 12
    DC32      0                                                 ; Reserved 13
    DC32      0                                                 ; Reserved 14
    DC32      0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m7-using-iar"></a><span data-ttu-id="11426-842">IAR을 사용하는 Cortex-M7의 모듈 속성</span><span class="sxs-lookup"><span data-stu-id="11426-842">Module properties for Cortex-M7 using IAR</span></span>

| <span data-ttu-id="11426-843">bit</span><span class="sxs-lookup"><span data-stu-id="11426-843">Bit</span></span> | <span data-ttu-id="11426-844">값</span><span class="sxs-lookup"><span data-stu-id="11426-844">Value</span></span> | <span data-ttu-id="11426-845">의미</span><span class="sxs-lookup"><span data-stu-id="11426-845">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="11426-846">0</span><span class="sxs-lookup"><span data-stu-id="11426-846">0</span></span> | <span data-ttu-id="11426-847">0</span><span class="sxs-lookup"><span data-stu-id="11426-847">0</span></span><br /><span data-ttu-id="11426-848">1</span><span class="sxs-lookup"><span data-stu-id="11426-848">1</span></span> | <span data-ttu-id="11426-849">권한 있는 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-849">Privileged mode execution</span></span><br /><span data-ttu-id="11426-850">사용자 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-850">User mode execution</span></span> |
| <span data-ttu-id="11426-851">1</span><span class="sxs-lookup"><span data-stu-id="11426-851">1</span></span> | <span data-ttu-id="11426-852">0</span><span class="sxs-lookup"><span data-stu-id="11426-852">0</span></span><br /><span data-ttu-id="11426-853">1</span><span class="sxs-lookup"><span data-stu-id="11426-853">1</span></span> | <span data-ttu-id="11426-854">MPU 보호 없음</span><span class="sxs-lookup"><span data-stu-id="11426-854">No MPU protection</span></span><br /><span data-ttu-id="11426-855">MPU 보호(사용자 모드가 선택되어 있어야 함)</span><span class="sxs-lookup"><span data-stu-id="11426-855">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="11426-856">2</span><span class="sxs-lookup"><span data-stu-id="11426-856">2</span></span> | <span data-ttu-id="11426-857">0</span><span class="sxs-lookup"><span data-stu-id="11426-857">0</span></span><br /><span data-ttu-id="11426-858">1</span><span class="sxs-lookup"><span data-stu-id="11426-858">1</span></span> | <span data-ttu-id="11426-859">공유/외부 메모리 액세스 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="11426-859">Disable shared/external memory access</span></span><br /><span data-ttu-id="11426-860">공유/외부 메모리 액세스 사용</span><span class="sxs-lookup"><span data-stu-id="11426-860">Enable shared/external memory access</span></span> |
| <span data-ttu-id="11426-861">[23-3]</span><span class="sxs-lookup"><span data-stu-id="11426-861">[23-3]</span></span> | <span data-ttu-id="11426-862">0</span><span class="sxs-lookup"><span data-stu-id="11426-862">0</span></span> | <span data-ttu-id="11426-863">예약됨</span><span class="sxs-lookup"><span data-stu-id="11426-863">Reserved</span></span>
| <span data-ttu-id="11426-864">[31-24]</span><span class="sxs-lookup"><span data-stu-id="11426-864">[31-24]</span></span> | <br /><span data-ttu-id="11426-865">0x00</span><span class="sxs-lookup"><span data-stu-id="11426-865">0x00</span></span><br /><span data-ttu-id="11426-866">0x01</span><span class="sxs-lookup"><span data-stu-id="11426-866">0x01</span></span><br /><span data-ttu-id="11426-867">0x02</span><span class="sxs-lookup"><span data-stu-id="11426-867">0x02</span></span> | <span data-ttu-id="11426-868">**컴파일러 ID**</span><span class="sxs-lookup"><span data-stu-id="11426-868">**Compiler ID**</span></span><br /><span data-ttu-id="11426-869">IAR</span><span class="sxs-lookup"><span data-stu-id="11426-869">IAR</span></span><br /><span data-ttu-id="11426-870">ARM</span><span class="sxs-lookup"><span data-stu-id="11426-870">ARM</span></span><br /><span data-ttu-id="11426-871">GNU</span><span class="sxs-lookup"><span data-stu-id="11426-871">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-iar"></a><span data-ttu-id="11426-872">IAR을 사용하는 Cortex-M7의 모듈 링커</span><span class="sxs-lookup"><span data-stu-id="11426-872">Module linker for Cortex-M7 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\cortex_v1_0.xml" */
/*-Specials-*/
define symbol __ICFEDIT_intvec_start__     = 0x00400000;
/*-Memory Regions-*/
define symbol __ICFEDIT_region_RAM_start__ = 0x20450000;
define symbol __ICFEDIT_region_RAM_end__   = 0x2045f000 -1;
define symbol __ICFEDIT_region_RAM_NOCACHE_start__ = 0x2045f000;
define symbol __ICFEDIT_region_RAM_NOCACHE_end__   = 0x20460000 -1;
define symbol __ICFEDIT_region_ROM_start__ = 0x00500000;
define symbol __ICFEDIT_region_ROM_end__   = 0x00600000 -1;
define symbol __ICFEDIT_region_SDRAM_start__ = 0x70000000;
define symbol __ICFEDIT_region_SDRAM_end__   = 0x70200000 -1;

/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__      = 0x2000;
define symbol __ICFEDIT_size_heap__        = 0x1000;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region RAM_region    = mem:[from __ICFEDIT_region_RAM_start__ to __ICFEDIT_region_RAM_end__];
define region RAM_NOCACHE_region = mem:[from __ICFEDIT_region_RAM_NOCACHE_start__ to __ICFEDIT_region_RAM_NOCACHE_end__];
define region ROM_region    = mem:[from __ICFEDIT_region_ROM_start__ to __ICFEDIT_region_ROM_end__];
define region SDRAM_region  = mem:[from __ICFEDIT_region_SDRAM_start__ to __ICFEDIT_region_SDRAM_end__];

define block HEAP   with alignment = 8, size = __ICFEDIT_size_heap__   { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

define movable block ROPI with alignment = 4, fixed order
{
  ro object txm_module_preamble.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-m7-using-iar"></a><span data-ttu-id="11426-873">IAR을 사용하는 Cortex-M7의 모듈 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-873">Building Modules for Cortex-M7 using IAR</span></span>

<span data-ttu-id="11426-874">예제 작업 영역이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="11426-874">An example workspace is provided.</span></span> <span data-ttu-id="11426-875">ThreadX 라이브러리, ThreadX 모듈 라이브러리, 데모 모듈 프로젝트 및 데모 모듈 관리자 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="11426-875">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m7-using-iar"></a><span data-ttu-id="11426-876">IAR을 사용하는 Cortex-M7의 스레드 확장 정의</span><span class="sxs-lookup"><span data-stu-id="11426-876">Thread extension definition for Cortex-M7 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_saved_lr;              \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-m7-using-iar"></a><span data-ttu-id="11426-877">IAR을 사용하는 Cortex-M7의 모듈 관리자 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-877">Building Module Manager for Cortex-M7 using IAR</span></span>

<span data-ttu-id="11426-878">예제 작업 영역이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="11426-878">An example workspace is provided.</span></span> <span data-ttu-id="11426-879">ThreadX 라이브러리, ThreadX 모듈 라이브러리, 데모 모듈 프로젝트 및 데모 모듈 관리자 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="11426-879">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-iar"></a><span data-ttu-id="11426-880">IAR을 사용하는 Cortex-M7의 외부 메모리 사용 API에 대한 특성</span><span class="sxs-lookup"><span data-stu-id="11426-880">Attributes for external memory enable API for Cortex-M7 using IAR</span></span>

<span data-ttu-id="11426-881">모듈에는 항상 공유 메모리에 대한 읽기 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-881">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="11426-882">특성 매개 변수</span><span class="sxs-lookup"><span data-stu-id="11426-882">Attribute parameter</span></span> | <span data-ttu-id="11426-883">의미</span><span class="sxs-lookup"><span data-stu-id="11426-883">Meaning</span></span> |
|---|---|
| <span data-ttu-id="11426-884">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="11426-884">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="11426-885">쓰기 액세스</span><span class="sxs-lookup"><span data-stu-id="11426-885">Write access</span></span> |

## <a name="cortex-r4-processor"></a><span data-ttu-id="11426-886">Cortex-R4 프로세서</span><span class="sxs-lookup"><span data-stu-id="11426-886">Cortex-R4 processor</span></span>

### <a name="cortex-r4-using-ac6"></a><span data-ttu-id="11426-887">AC6을 사용하는 Cortex-R4</span><span class="sxs-lookup"><span data-stu-id="11426-887">Cortex-R4 using AC6</span></span>

#### <a name="module-preamble-for-cortex-r4-using-ac6"></a><span data-ttu-id="11426-888">AC6을 사용하는 Cortex-R4의 모듈 머리말</span><span class="sxs-lookup"><span data-stu-id="11426-888">Module preamble for Cortex-R4 using AC6</span></span>

```c
    .text

/* Define common external references.  */

.global     _txm_module_thread_shell_entry
.global     demo_module_start
.global     _txm_module_callback_request_thread_entry
.global     Image$$ER_RO$$Length
.global     Image$$ER_RW$$Length
.global     Image$$ER_ZI$$ZI$$Length

/* Stack aligned, ROPI and RWPI, R9 used as data offset register.  */
.eabi_attribute Tag_ABI_align_preserved, 1
.eabi_attribute Tag_ABI_PCS_RO_data, 1
.eabi_attribute Tag_ABI_PCS_R9_use,  1
.eabi_attribute Tag_ABI_PCS_RW_data, 2

__txm_module_preamble:
.word   0x4D4F4455                                          /* Module ID  */
.word   0x5                                                 /* Module Major Version  */
.word   0x3                                                 /* Module Minor Version  */
.word   32                                                  /* Module Preamble Size in 32-bit words  */
.word   0x12345678                                          /* Module ID (application defined)  */
.word   0x01000001                                          /* Module Properties where:
                                                               Bits 31-24: Compiler ID
                                                                       0 -> IAR
                                                                       1 -> RVDS/ARM
                                                                       2 -> GNU
                                                               Bits 23-1:  Reserved
                                                               Bit 0:  0 -> Privileged mode execution (no MMU protection)
                                                                       1 -> User mode execution (MMU protection)  */
.word   _txm_module_thread_shell_entry - __txm_module_preamble  /* Module Shell Entry Point  */
.word   demo_module_start - __txm_module_preamble           /* Module Start Thread Entry Point  */
.word   0                                                   /* Module Stop Thread Entry Point   */
.word   1                                                   /* Module Start/Stop Thread Priority  */
.word   1024                                                /* Module Start/Stop Thread Stack Size  */
.word   _txm_module_callback_request_thread_entry - __txm_module_preamble   /* Module Callback Thread Entry  */
.word   1                                                   /* Module Callback Thread Priority  */
.word   1024                                                /* Module Callback Thread Stack Size  */
.word   9000                                                /* Module Code Size */
.word   11000                                               /* Module Data Size */
.word   0                                                   /* Reserved 0  */
.word   0                                                   /* Reserved 1  */
.word   0                                                   /* Reserved 2  */
.word   0                                                   /* Reserved 3  */
.word   0                                                   /* Reserved 4  */
.word   0                                                   /* Reserved 5  */
.word   0                                                   /* Reserved 6  */
.word   0                                                   /* Reserved 7  */
.word   0                                                   /* Reserved 8  */
.word   0                                                   /* Reserved 9  */
.word   0                                                   /* Reserved 10  */
.word   0                                                   /* Reserved 11  */
.word   0                                                   /* Reserved 12  */
.word   0                                                   /* Reserved 13  */
.word   0                                                   /* Reserved 14  */
.word   0                                                   /* Reserved 15  */
```

#### <a name="module-properties-for-cortex-r4-using-ac6"></a><span data-ttu-id="11426-889">AC6을 사용하는 Cortex-R4의 모듈 속성</span><span class="sxs-lookup"><span data-stu-id="11426-889">Module properties for Cortex-R4 using AC6</span></span>

| <span data-ttu-id="11426-890">bit</span><span class="sxs-lookup"><span data-stu-id="11426-890">Bit</span></span> | <span data-ttu-id="11426-891">값</span><span class="sxs-lookup"><span data-stu-id="11426-891">Value</span></span> | <span data-ttu-id="11426-892">의미</span><span class="sxs-lookup"><span data-stu-id="11426-892">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="11426-893">0</span><span class="sxs-lookup"><span data-stu-id="11426-893">0</span></span> | <span data-ttu-id="11426-894">0</span><span class="sxs-lookup"><span data-stu-id="11426-894">0</span></span><br /><span data-ttu-id="11426-895">1</span><span class="sxs-lookup"><span data-stu-id="11426-895">1</span></span> | <span data-ttu-id="11426-896">권한 있는 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-896">Privileged mode execution</span></span><br /><span data-ttu-id="11426-897">사용자 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-897">User mode execution</span></span> |
| <span data-ttu-id="11426-898">[23-1]</span><span class="sxs-lookup"><span data-stu-id="11426-898">[23-1]</span></span> | <span data-ttu-id="11426-899">0</span><span class="sxs-lookup"><span data-stu-id="11426-899">0</span></span> | <span data-ttu-id="11426-900">예약됨</span><span class="sxs-lookup"><span data-stu-id="11426-900">Reserved</span></span>
| <span data-ttu-id="11426-901">[31-24]</span><span class="sxs-lookup"><span data-stu-id="11426-901">[31-24]</span></span> | <br /><span data-ttu-id="11426-902">0x00</span><span class="sxs-lookup"><span data-stu-id="11426-902">0x00</span></span><br /><span data-ttu-id="11426-903">0x01</span><span class="sxs-lookup"><span data-stu-id="11426-903">0x01</span></span><br /><span data-ttu-id="11426-904">0x02</span><span class="sxs-lookup"><span data-stu-id="11426-904">0x02</span></span> | <span data-ttu-id="11426-905">**컴파일러 ID**</span><span class="sxs-lookup"><span data-stu-id="11426-905">**Compiler ID**</span></span><br /><span data-ttu-id="11426-906">IAR</span><span class="sxs-lookup"><span data-stu-id="11426-906">IAR</span></span><br /><span data-ttu-id="11426-907">ARM</span><span class="sxs-lookup"><span data-stu-id="11426-907">ARM</span></span><br /><span data-ttu-id="11426-908">GNU</span><span class="sxs-lookup"><span data-stu-id="11426-908">GNU</span></span> |

#### <a name="module-linker-for-cortex-r4-using-ac6"></a><span data-ttu-id="11426-909">AC6을 사용하는 Cortex-R4의 모듈 링커</span><span class="sxs-lookup"><span data-stu-id="11426-909">Module linker for Cortex-R4 using AC6</span></span>

<span data-ttu-id="11426-910">명령줄을 기반으로 하며 링커 파일 예제는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-910">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-cortex-r4-using-ac6"></a><span data-ttu-id="11426-911">AC6을 사용하는 Cortex-R4의 모듈 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-911">Building Modules for Cortex-R4 using AC6</span></span>

<span data-ttu-id="11426-912">AC6을 사용하여 Cortex-R4 모듈을 빌드하는 간단한 명령줄 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-912">A simple command-line example for building a Cortex-R4 module using AC6:</span></span>

```dos
armclang -c -g -fropi -frwpi --target=arm-arm-none-eabi -mcpu=cortex-r4 demo_threadx_module.c
armclang -c -g -fropi -frwpi --target=arm-arm-none-eabi -mcpu=cortex-r4 txm_module_preamble.S
armclang -c -g -fropi -frwpi --target=arm-arm-none-eabi -mcpu=cortex-r4 semihosting.c
armlink -d -o demo_threadx_module.axf --elf --ro 0x00100000 --first txm_module_preamble.o --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --datacompressor=off --list demo_threadx_module.map txm_module_preamble.o demo_threadx_module.o semihosting.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-r4-using-ac6"></a><span data-ttu-id="11426-913">AC6을 사용하는 Cortex-R4의 스레드 확장 정의</span><span class="sxs-lookup"><span data-stu-id="11426-913">Thread extension definition for Cortex-R4 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2   ULONG   tx_thread_vfp_enable;                   \
                                VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-r4-using-ac6"></a><span data-ttu-id="11426-914">AC6을 사용하는 Cortex-R4의 모듈 관리자 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-914">Building Module Manager for Cortex-R4 using AC6</span></span>

<span data-ttu-id="11426-915">AC6을 사용하여 Cortex-R4 모듈 관리자를 빌드하는 간단한 명령줄 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-915">A simple command-line example for building a Cortex-R4 module manager using AC6:</span></span>

```dos
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 demo_threadx_module_manager.c
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 timer.c
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 gic.c
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 tx_initialize_low_level.S
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 startup.S
armlink -d -o demo_threadx_module_manager.axf --elf --scatter=demo_threadx.scat --remove --map --symbols --list demo_threadx_module_manager.map startup.o timer.o gic.o demo_threadx_module_manager.o tx_initialize_low_level.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-r4-using-ac6"></a><span data-ttu-id="11426-916">AC6을 사용하는 Cortex-R4의 외부 메모리 사용 API에 대한 특성</span><span class="sxs-lookup"><span data-stu-id="11426-916">Attributes for external memory enable API for Cortex-R4 using AC6</span></span>

<span data-ttu-id="11426-917">모듈에는 항상 공유 메모리에 대한 읽기 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-917">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="11426-918">특성 매개 변수</span><span class="sxs-lookup"><span data-stu-id="11426-918">Attribute parameter</span></span> | <span data-ttu-id="11426-919">의미</span><span class="sxs-lookup"><span data-stu-id="11426-919">Meaning</span></span> |
|---|---|
| <span data-ttu-id="11426-920">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="11426-920">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="11426-921">쓰기 액세스</span><span class="sxs-lookup"><span data-stu-id="11426-921">Write access</span></span> |

### <a name="cortex-r4-using-iar"></a><span data-ttu-id="11426-922">IAR을 사용하는 Cortex-R4</span><span class="sxs-lookup"><span data-stu-id="11426-922">Cortex-R4 using IAR</span></span>

#### <a name="module-preamble-for-cortex-r4-using-iar"></a><span data-ttu-id="11426-923">IAR을 사용하는 Cortex-R4의 모듈 머리말</span><span class="sxs-lookup"><span data-stu-id="11426-923">Module preamble for Cortex-R4 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */
    PUBLIC __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    EXTERN demo_module_start

    /* Define common external references.  */
    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        ; Module ID
    DC32      0x5                                               ; Module Major Version
    DC32      0x6                                               ; Module Minor Version
    DC32      32                                                ; Module Preamble Size in 32-bit words
    DC32      0x12345678                                        ; Module ID (application defined)
    DC32      0x00000001                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-1: Reserved
                                                                ;   Bit 0:  0 -> Privileged mode execution (no MPU protection)
                                                                ;           1 -> User mode execution (MPU protection)
    DC32      _txm_module_thread_shell_entry - . - 0            ; Module Shell Entry Point
    DC32      demo_module_start - . - 0                         ; Module Start Thread Entry Point
    DC32      0                                                 ; Module Stop Thread Entry Point
    DC32      1                                                 ; Module Start/Stop Thread Priority
    DC32      1024                                              ; Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 ; Module Callback Thread Entry
    DC32      1                                                 ; Module Callback Thread Priority
    DC32      1024                                              ; Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      ; Module Code Size
    DC32      RWPI$$Length                                      ; Module Data Size
    DC32      0                                                 ; Reserved 0
    DC32      0                                                 ; Reserved 1
    DC32      0                                                 ; Reserved 2
    DC32      0                                                 ; Reserved 3
    DC32      0                                                 ; Reserved 4
    DC32      0                                                 ; Reserved 5
    DC32      0                                                 ; Reserved 6
    DC32      0                                                 ; Reserved 7
    DC32      0                                                 ; Reserved 8  
    DC32      0                                                 ; Reserved 9
    DC32      0                                                 ; Reserved 10
    DC32      0                                                 ; Reserved 11
    DC32      0                                                 ; Reserved 12
    DC32      0                                                 ; Reserved 13
    DC32      0                                                 ; Reserved 14
    DC32      0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-r4-using-iar"></a><span data-ttu-id="11426-924">IAR을 사용하는 Cortex-R4의 모듈 속성</span><span class="sxs-lookup"><span data-stu-id="11426-924">Module properties for Cortex-R4 using IAR</span></span>

| <span data-ttu-id="11426-925">bit</span><span class="sxs-lookup"><span data-stu-id="11426-925">Bit</span></span> | <span data-ttu-id="11426-926">값</span><span class="sxs-lookup"><span data-stu-id="11426-926">Value</span></span> | <span data-ttu-id="11426-927">의미</span><span class="sxs-lookup"><span data-stu-id="11426-927">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="11426-928">0</span><span class="sxs-lookup"><span data-stu-id="11426-928">0</span></span> | <span data-ttu-id="11426-929">0</span><span class="sxs-lookup"><span data-stu-id="11426-929">0</span></span><br /><span data-ttu-id="11426-930">1</span><span class="sxs-lookup"><span data-stu-id="11426-930">1</span></span> | <span data-ttu-id="11426-931">권한 있는 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-931">Privileged mode execution</span></span><br /><span data-ttu-id="11426-932">사용자 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-932">User mode execution</span></span> |
| <span data-ttu-id="11426-933">[23-1]</span><span class="sxs-lookup"><span data-stu-id="11426-933">[23-1]</span></span> | <span data-ttu-id="11426-934">0</span><span class="sxs-lookup"><span data-stu-id="11426-934">0</span></span> | <span data-ttu-id="11426-935">예약됨</span><span class="sxs-lookup"><span data-stu-id="11426-935">Reserved</span></span>
| <span data-ttu-id="11426-936">[31-24]</span><span class="sxs-lookup"><span data-stu-id="11426-936">[31-24]</span></span> | <br /><span data-ttu-id="11426-937">0x00</span><span class="sxs-lookup"><span data-stu-id="11426-937">0x00</span></span><br /><span data-ttu-id="11426-938">0x01</span><span class="sxs-lookup"><span data-stu-id="11426-938">0x01</span></span><br /><span data-ttu-id="11426-939">0x02</span><span class="sxs-lookup"><span data-stu-id="11426-939">0x02</span></span> | <span data-ttu-id="11426-940">**컴파일러 ID**</span><span class="sxs-lookup"><span data-stu-id="11426-940">**Compiler ID**</span></span><br /><span data-ttu-id="11426-941">IAR</span><span class="sxs-lookup"><span data-stu-id="11426-941">IAR</span></span><br /><span data-ttu-id="11426-942">ARM</span><span class="sxs-lookup"><span data-stu-id="11426-942">ARM</span></span><br /><span data-ttu-id="11426-943">GNU</span><span class="sxs-lookup"><span data-stu-id="11426-943">GNU</span></span> |

#### <a name="module-linker-for-cortex-r4-using-iar"></a><span data-ttu-id="11426-944">IAR을 사용하는 Cortex-R4의 모듈 링커</span><span class="sxs-lookup"><span data-stu-id="11426-944">Module linker for Cortex-R4 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\a_v1_0.xml" */
/*-Specials-*/
/*-Memory Regions-*/
define symbol __ICFEDIT_region_ROM_start__ = 0x00100000;
define symbol __ICFEDIT_region_ROM_end__   = 0x0013FFFF;
define symbol __ICFEDIT_region_RAM_start__ = 0x08000000;
define symbol __ICFEDIT_region_RAM_end__   = 0x0800FFFF;
/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__   = 0;
define symbol __ICFEDIT_size_svcstack__ = 0;
define symbol __ICFEDIT_size_irqstack__ = 0;
define symbol __ICFEDIT_size_fiqstack__ = 0;
define symbol __ICFEDIT_size_undstack__ = 0;
define symbol __ICFEDIT_size_abtstack__ = 0;
define symbol __ICFEDIT_size_heap__     = 0x100;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region ROM_region   = mem:[from __ICFEDIT_region_ROM_start__   to __ICFEDIT_region_ROM_end__];
define region RAM_region   = mem:[from __ICFEDIT_region_RAM_start__   to __ICFEDIT_region_RAM_end__];

define block HEAP      with alignment = 8, size = __ICFEDIT_size_heap__     { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

define movable block ROPI with alignment = 4, fixed order
{
  ro object txm_module_preamble.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-r4-using-iar"></a><span data-ttu-id="11426-945">IAR을 사용하는 Cortex-R4의 모듈 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-945">Building Modules for Cortex-R4 using IAR</span></span>

<span data-ttu-id="11426-946">예제 작업 영역이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="11426-946">An example workspace is provided.</span></span> <span data-ttu-id="11426-947">ThreadX 라이브러리, ThreadX 모듈 라이브러리, 데모 모듈 프로젝트 및 데모 모듈 관리자 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="11426-947">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-r4-using-iar"></a><span data-ttu-id="11426-948">IAR을 사용하는 Cortex-R4의 스레드 확장 정의</span><span class="sxs-lookup"><span data-stu-id="11426-948">Thread extension definition for Cortex-R4 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   ULONG   tx_thread_vfp_enable;                   \
                                VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-r4-using-iar"></a><span data-ttu-id="11426-949">IAR을 사용하는 Cortex-R4의 모듈 관리자 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-949">Building Module Manager for Cortex-R4 using IAR</span></span>

<span data-ttu-id="11426-950">예제 작업 영역이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="11426-950">An example workspace is provided.</span></span> <span data-ttu-id="11426-951">ThreadX 라이브러리, ThreadX 모듈 라이브러리, 데모 모듈 프로젝트 및 데모 모듈 관리자 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="11426-951">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-r4-using-iar"></a><span data-ttu-id="11426-952">IAR을 사용하는 Cortex-R4의 외부 메모리 사용 API에 대한 특성</span><span class="sxs-lookup"><span data-stu-id="11426-952">Attributes for external memory enable API for Cortex-R4 using IAR</span></span>

<span data-ttu-id="11426-953">모듈에는 항상 공유 메모리에 대한 읽기 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-953">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="11426-954">특성 매개 변수</span><span class="sxs-lookup"><span data-stu-id="11426-954">Attribute parameter</span></span> | <span data-ttu-id="11426-955">의미</span><span class="sxs-lookup"><span data-stu-id="11426-955">Meaning</span></span> |
|---|---|
| <span data-ttu-id="11426-956">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="11426-956">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="11426-957">쓰기 액세스</span><span class="sxs-lookup"><span data-stu-id="11426-957">Write access</span></span> |

## <a name="mcf544xx-processor"></a><span data-ttu-id="11426-958">MCF544xx 프로세서</span><span class="sxs-lookup"><span data-stu-id="11426-958">MCF544xx processor</span></span>

### <a name="mcf544xx-using-ghs"></a><span data-ttu-id="11426-959">GHS를 사용하는 MCF544xx</span><span class="sxs-lookup"><span data-stu-id="11426-959">MCF544xx using GHS</span></span>

#### <a name="module-preamble-for-mcf544xx-using-ghs"></a><span data-ttu-id="11426-960">GHS를 사용하는 MCF544xx의 모듈 머리말</span><span class="sxs-lookup"><span data-stu-id="11426-960">Module preamble for MCF544xx using GHS</span></span>

```c
    SECT    .preamble, x

    /* Define public symbols.  */
    XDEF __txm_module_preamble

__txm_module_preamble:
    DC.L    0x4D4F4455                                  /* Module ID                                */
    DC.L    0x5                                         /* Module Major Version                     */
    DC.L    0x3                                         /* Module Minor Version                     */
    DC.L    32                                          /* Module Preamble Size in 32-bit words     */
    DC.L    0x12345678                                  /* Module ID (application defined)          */
    DC.L    0x03000003                                  /* Module Properties where:                 */
                                                        /* Bits 31-24: Compiler ID                  */
                                                        /*           3 -> GHS                       */
                                                        /* Bits 23-2: Reserved                      */
                                                        /* Bit 1:  0 -> No MMU protection           */
                                                        /*         1 -> MMU protection (must have   */
                                                        /*              user mode selected)         */
                                                        /* Bit 0:  0 -> Supervisor mode execution   */
                                                        /*         1 -> User mode execution         */
    DC.L    _txm_module_thread_shell_entry              /* Module Shell Entry Point                 */
    DC.L    demo_module_start                           /* Module Start Thread Entry Point          */
    DC.L    0                                           /* Module Stop Thread Entry Point           */
    DC.L    1                                           /* Module Start/Stop Thread Priority        */
    DC.L    2048                                        /* Module Start/Stop Thread Stack Size      */
    DC.L    _txm_module_callback_request_thread_entry   /* Module Callback Thread Entry             */
    DC.L    1                                           /* Module Callback Thread Priority          */
    DC.L    2048                                        /* Module Callback Thread Stack Size        */
    DC.L    module_code_size                            /* Module Code Size                         */
    DC.L    module_data_size                            /* Module Data Size                         */
    DC.L    0                                           /* Reserved 0                               */
    DC.L    0                                           /* Reserved 1                               */
    DC.L    0                                           /* Reserved 2                               */
    DC.L    0                                           /* Reserved 3                               */
    DC.L    0                                           /* Reserved 4                               */
    DC.L    0                                           /* Reserved 5                               */
    DC.L    0                                           /* Reserved 6                               */
    DC.L    0                                           /* Reserved 7                               */
    DC.L    0                                           /* Reserved 8                               */
    DC.L    0                                           /* Reserved 9                               */
    DC.L    0                                           /* Reserved 10                              */
    DC.L    0                                           /* Reserved 11                              */
    DC.L    0                                           /* Reserved 12                              */
    DC.L    0                                           /* Reserved 13                              */
    DC.L    0                                           /* Reserved 14                              */
    DC.L    0                                           /* Reserved 15                              */

    END
```

#### <a name="module-properties-for-mcf544xx-using-ghs"></a><span data-ttu-id="11426-961">GHS를 사용하는 MCF544xx의 모듈 속성</span><span class="sxs-lookup"><span data-stu-id="11426-961">Module properties for MCF544xx using GHS</span></span>

| <span data-ttu-id="11426-962">bit</span><span class="sxs-lookup"><span data-stu-id="11426-962">Bit</span></span> | <span data-ttu-id="11426-963">값</span><span class="sxs-lookup"><span data-stu-id="11426-963">Value</span></span> | <span data-ttu-id="11426-964">의미</span><span class="sxs-lookup"><span data-stu-id="11426-964">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="11426-965">0</span><span class="sxs-lookup"><span data-stu-id="11426-965">0</span></span> | <span data-ttu-id="11426-966">0</span><span class="sxs-lookup"><span data-stu-id="11426-966">0</span></span><br /><span data-ttu-id="11426-967">1</span><span class="sxs-lookup"><span data-stu-id="11426-967">1</span></span> | <span data-ttu-id="11426-968">권한 있는 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-968">Privileged mode execution</span></span><br /><span data-ttu-id="11426-969">사용자 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-969">User mode execution</span></span> |
| <span data-ttu-id="11426-970">1</span><span class="sxs-lookup"><span data-stu-id="11426-970">1</span></span> | <span data-ttu-id="11426-971">0</span><span class="sxs-lookup"><span data-stu-id="11426-971">0</span></span><br /><span data-ttu-id="11426-972">1</span><span class="sxs-lookup"><span data-stu-id="11426-972">1</span></span> | <span data-ttu-id="11426-973">MMU 보호 없음</span><span class="sxs-lookup"><span data-stu-id="11426-973">No MMU protection</span></span><br /><span data-ttu-id="11426-974">MMU 보호(사용자 모드가 선택되어 있어야 함)</span><span class="sxs-lookup"><span data-stu-id="11426-974">MMU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="11426-975">2</span><span class="sxs-lookup"><span data-stu-id="11426-975">2</span></span> | <span data-ttu-id="11426-976">0</span><span class="sxs-lookup"><span data-stu-id="11426-976">0</span></span><br /><span data-ttu-id="11426-977">1</span><span class="sxs-lookup"><span data-stu-id="11426-977">1</span></span> | <span data-ttu-id="11426-978">공유/외부 메모리 액세스 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="11426-978">Disable shared/external memory access</span></span><br /><span data-ttu-id="11426-979">공유/외부 메모리 액세스 사용</span><span class="sxs-lookup"><span data-stu-id="11426-979">Enable shared/external memory access</span></span> |
| <span data-ttu-id="11426-980">[23-3]</span><span class="sxs-lookup"><span data-stu-id="11426-980">[23-3]</span></span> | <span data-ttu-id="11426-981">0</span><span class="sxs-lookup"><span data-stu-id="11426-981">0</span></span> | <span data-ttu-id="11426-982">예약됨</span><span class="sxs-lookup"><span data-stu-id="11426-982">Reserved</span></span>
| <span data-ttu-id="11426-983">[31-24]</span><span class="sxs-lookup"><span data-stu-id="11426-983">[31-24]</span></span> | <br /><span data-ttu-id="11426-984">0x03</span><span class="sxs-lookup"><span data-stu-id="11426-984">0x03</span></span> | <span data-ttu-id="11426-985">**컴파일러 ID**</span><span class="sxs-lookup"><span data-stu-id="11426-985">**Compiler ID**</span></span><br /><span data-ttu-id="11426-986">GHS</span><span class="sxs-lookup"><span data-stu-id="11426-986">GHS</span></span> |

#### <a name="module-linker-for-mcf544xx-using-ghs"></a><span data-ttu-id="11426-987">GHS를 사용하는 MCF544xx의 모듈 링커</span><span class="sxs-lookup"><span data-stu-id="11426-987">Module linker for MCF544xx using GHS</span></span>

```c
DEFAULTS {

    heap_reserve =  256
    stack_reserve = 256
}

//
// Program layout for PIC and PID built programs.
//

-sec
{
//
// The data segment
//
    .pidbase                0x00000000 :
    .sdabase                           :
    .sbss                   NOCLEAR    :
    .sdata                             :
    .data                   NOLOAD     :
    .bss                    NOCLEAR    :
    .heap                   ALIGN(16) PAD( heap_reserve +
        // Add space for call-graph profiling if used:
        (isdefined(__ghs_indgcount)?(2000+(sizeof(.text)/2)):0) +
        // Add estimated space for call-count profiling if used:
        (isdefined(__ghs_indmcount)?10000:0) )
                                             :
    .stack      ALIGN(16) PAD(stack_reserve) :

    module_data_size = sizeof(.pidbase) + sizeof(.sdabase) + sizeof(.sbss) + sizeof(.sdata) + sizeof(.data) + sizeof(.bss) + sizeof(.heap) + sizeof(.stack);

//
// The code segment
//

    .picbase                0x00000000 :
    .preamble                          :
    .text                              :
    .syscall                           :
    .fixaddr                           :
    .fixtype                           :
    .rodata                            :
    .ROM.data               ROM(.data) :
    .secinfo                           :

    module_code_size =  endaddr(.secinfo);
}
```

#### <a name="building-modules-for-mcf544xx-using-ghs"></a><span data-ttu-id="11426-988">GHS를 사용하는 MCF544xx의 모듈 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-988">Building Modules for MCF544xx using GHS</span></span>

<span data-ttu-id="11426-989">예제 작업 영역이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="11426-989">An example workspace is provided.</span></span> <span data-ttu-id="11426-990">ThreadX 라이브러리, ThreadX 모듈 라이브러리, 데모 모듈 프로젝트 및 데모 모듈 관리자 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="11426-990">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-mcf544xx-using-ghs"></a><span data-ttu-id="11426-991">GHS를 사용하는 MCF544xx의 스레드 확장 정의</span><span class="sxs-lookup"><span data-stu-id="11426-991">Thread extension definition for MCF544xx using GHS</span></span>

```c
#define TX_THREAD_EXTENSION_2   int     Errno;                                  \
                                VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_mmu_protection;        \
                                VOID *  tx_thread_module_dispatch_return;       \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-mcf544xx-using-ghs"></a><span data-ttu-id="11426-992">GHS를 사용하는 MCF544xx의 모듈 관리자 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-992">Building Module Manager for MCF544xx using GHS</span></span>

<span data-ttu-id="11426-993">예제 작업 영역이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="11426-993">An example workspace is provided.</span></span> <span data-ttu-id="11426-994">ThreadX 라이브러리, ThreadX 모듈 라이브러리, 데모 모듈 프로젝트 및 데모 모듈 관리자 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="11426-994">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-mcf544xx-using-ghs"></a><span data-ttu-id="11426-995">GHS를 사용하는 MCF544xx의 외부 메모리 사용 API에 대한 특성</span><span class="sxs-lookup"><span data-stu-id="11426-995">Attributes for external memory enable API for MCF544xx using GHS</span></span>

<span data-ttu-id="11426-996">이 기능은 MCF544xx에서 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="11426-996">This feature not enabled on MCF544xx.</span></span>

## <a name="rx63-processor"></a><span data-ttu-id="11426-997">RX63 프로세서</span><span class="sxs-lookup"><span data-stu-id="11426-997">RX63 processor</span></span>

### <a name="rx63-using-iar"></a><span data-ttu-id="11426-998">IAR을 사용하는 RX63</span><span class="sxs-lookup"><span data-stu-id="11426-998">RX63 using IAR</span></span>

#### <a name="module-preamble-for-rx63-using-iar"></a><span data-ttu-id="11426-999">IAR을 사용하는 RX63의 모듈 머리말</span><span class="sxs-lookup"><span data-stu-id="11426-999">Module preamble for RX63 using IAR</span></span>

```c
    /* Alignment of 4 (16-byte) */
    SECTION .text:CODE (4)

    /* Define public symbols.  */
    PUBLIC __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    EXTERN _demo_module_start

    /* Define common external references.  */
    EXTERN  __txm_module_thread_shell_entry
    EXTERN  __txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        // Module ID
    DC32      0x5                                               // Module Major Version
    DC32      0x6                                               // Module Minor Version
    DC32      32                                                // Module Preamble Size in 32-bit words
    DC32      0x12345678                                        // Module ID (application defined)
    DC32      0x00000007                                        // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    DC32      __txm_module_thread_shell_entry - $               // Module Shell Entry Point
    DC32      _demo_module_start - $                            // Module Start Thread Entry Point
    DC32      0                                                 // Module Stop Thread Entry Point
    DC32      1                                                 // Module Start/Stop Thread Priority
    DC32      1024                                              // Module Start/Stop Thread Stack Size
    DC32      __txm_module_callback_request_thread_entry - $    // Module Callback Thread Entry
    DC32      1                                                 // Module Callback Thread Priority
    DC32      1024                                              // Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      // Module Code Size
    DC32      RWPI$$Length                                      // Module Data Size
    DC32      0                                                 // Reserved 0
    DC32      0                                                 // Reserved 1
    DC32      0                                                 // Reserved 2
    DC32      0                                                 // Reserved 3
    DC32      0                                                 // Reserved 4
    DC32      0                                                 // Reserved 5
    DC32      0                                                 // Reserved 6
    DC32      0                                                 // Reserved 7
    DC32      0                                                 // Reserved 8  
    DC32      0                                                 // Reserved 9
    DC32      0                                                 // Reserved 10
    DC32      0                                                 // Reserved 11
    DC32      0                                                 // Reserved 12
    DC32      0                                                 // Reserved 13
    DC32      0                                                 // Reserved 14
    DC32      0                                                 // Reserved 15

    END
```

#### <a name="module-properties-for-rx63-using-iar"></a><span data-ttu-id="11426-1000">IAR을 사용하는 RX63의 모듈 속성</span><span class="sxs-lookup"><span data-stu-id="11426-1000">Module properties for RX63 using IAR</span></span>

| <span data-ttu-id="11426-1001">bit</span><span class="sxs-lookup"><span data-stu-id="11426-1001">Bit</span></span> | <span data-ttu-id="11426-1002">값</span><span class="sxs-lookup"><span data-stu-id="11426-1002">Value</span></span> | <span data-ttu-id="11426-1003">의미</span><span class="sxs-lookup"><span data-stu-id="11426-1003">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="11426-1004">0</span><span class="sxs-lookup"><span data-stu-id="11426-1004">0</span></span> | <span data-ttu-id="11426-1005">0</span><span class="sxs-lookup"><span data-stu-id="11426-1005">0</span></span><br /><span data-ttu-id="11426-1006">1</span><span class="sxs-lookup"><span data-stu-id="11426-1006">1</span></span> | <span data-ttu-id="11426-1007">권한 있는 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-1007">Privileged mode execution</span></span><br /><span data-ttu-id="11426-1008">사용자 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-1008">User mode execution</span></span> |
| <span data-ttu-id="11426-1009">1</span><span class="sxs-lookup"><span data-stu-id="11426-1009">1</span></span> | <span data-ttu-id="11426-1010">0</span><span class="sxs-lookup"><span data-stu-id="11426-1010">0</span></span><br /><span data-ttu-id="11426-1011">1</span><span class="sxs-lookup"><span data-stu-id="11426-1011">1</span></span> | <span data-ttu-id="11426-1012">MPU 보호 없음</span><span class="sxs-lookup"><span data-stu-id="11426-1012">No MPU protection</span></span><br /><span data-ttu-id="11426-1013">MPU 보호(사용자 모드가 선택되어 있어야 함)</span><span class="sxs-lookup"><span data-stu-id="11426-1013">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="11426-1014">2</span><span class="sxs-lookup"><span data-stu-id="11426-1014">2</span></span> | <span data-ttu-id="11426-1015">0</span><span class="sxs-lookup"><span data-stu-id="11426-1015">0</span></span><br /><span data-ttu-id="11426-1016">1</span><span class="sxs-lookup"><span data-stu-id="11426-1016">1</span></span> | <span data-ttu-id="11426-1017">공유/외부 메모리 액세스 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="11426-1017">Disable shared/external memory access</span></span><br /><span data-ttu-id="11426-1018">공유/외부 메모리 액세스 사용</span><span class="sxs-lookup"><span data-stu-id="11426-1018">Enable shared/external memory access</span></span> |
| <span data-ttu-id="11426-1019">[23-3]</span><span class="sxs-lookup"><span data-stu-id="11426-1019">[23-3]</span></span> | <span data-ttu-id="11426-1020">0</span><span class="sxs-lookup"><span data-stu-id="11426-1020">0</span></span> | <span data-ttu-id="11426-1021">예약됨</span><span class="sxs-lookup"><span data-stu-id="11426-1021">Reserved</span></span>
| <span data-ttu-id="11426-1022">[31-24]</span><span class="sxs-lookup"><span data-stu-id="11426-1022">[31-24]</span></span> | <br /><span data-ttu-id="11426-1023">0x00</span><span class="sxs-lookup"><span data-stu-id="11426-1023">0x00</span></span><br /><span data-ttu-id="11426-1024">0x02</span><span class="sxs-lookup"><span data-stu-id="11426-1024">0x02</span></span> | <span data-ttu-id="11426-1025">**컴파일러 ID**</span><span class="sxs-lookup"><span data-stu-id="11426-1025">**Compiler ID**</span></span><br /><span data-ttu-id="11426-1026">IAR</span><span class="sxs-lookup"><span data-stu-id="11426-1026">IAR</span></span><br /><span data-ttu-id="11426-1027">GNU</span><span class="sxs-lookup"><span data-stu-id="11426-1027">GNU</span></span> |

#### <a name="module-linker-for-rx63-using-iar"></a><span data-ttu-id="11426-1028">IAR을 사용하는 RX63의 모듈 링커</span><span class="sxs-lookup"><span data-stu-id="11426-1028">Module linker for RX63 using IAR</span></span>

```c
//-----------------------------------------------------------------------------
// ILINK command file template for the Renesas RX microcontroller R5F563NB
//-----------------------------------------------------------------------------
define exported symbol __link_file_version_4 = 1;

define memory mem with size = 4G;

// ID Code Protection
define exported symbol __ID_BYTES_1_4   = 0xFFFFFFFF;
define exported symbol __ID_BYTES_5_8   = 0xFFFFFFFF;
define exported symbol __ID_BYTES_9_12  = 0xFFFFFFFF;
define exported symbol __ID_BYTES_13_16 = 0xFFFFFFFF;

// Endian Select Register (MDE)
// Choose between Little endian=0xFFFFFFFF or Big endian=0xFFFFFFF8
define exported symbol __MDES           = 0xFFFFFFFF;

// Option Function Select Register 0 (OFS0)
define exported symbol __OFS0           = 0xFFFFFFFF;

// Option Function Select Register 1 (OFS1)
define exported symbol __OFS1           = 0xFFFFFFFF;

//define region ROM_region16 = mem:[from 0xFFFF8000 to 0xFFFFFFFF];
define region RAM_region16 = mem:[from 0x00010000 to 0x00017FFF];
//define region ROM_region24 = mem:[from 0xFFF00000 to 0xFFFFFFFF];
//define region RAM_region24 = mem:[from 0x00000004 to 0x0001FFFF];
define region ROM_region32 = mem:[from 0xFFF10400 to 0xFFFFFFFF];
//define region RAM_region32 = mem:[from 0x00000004 to 0x0001FFFF];
//define region DATA_FLASH_region = mem:[from 0x00100000 to 0x00107FFF];

initialize by copy { rw, ro section D, ro section D_1, ro section D_2 };
do not initialize  { section .*.noinit };

define block HEAP     with alignment = 4, size = _HEAP_SIZE { };
//define block USTACK   with alignment = 4, size = _USTACK_SIZE { };
//define block ISTACK   with alignment = 4, size = _ISTACK_SIZE { };

//define block STACKS with fixed order { block ISTACK,
//                                       block USTACK };

//place at address mem:0xFFFFFF80 { ro section .nmivec };
//"ROM16":place in ROM_region16        { ro section .code16*,
//                                       ro section .data16* };
//"RAM16":place in RAM_region16        { rw section .data16*,
//                                       rw section __DLIB_PERTHREAD };
//"ROM24":place in ROM_region24        { ro section .code24*,
//                                       ro section .data24* };
//"RAM24":place in RAM_region24        { rw section .data24* };
//"ROM32":place in ROM_region32        { ro };
//"RAM32":place in RAM_region32        { rw,
//                                       ro section D,
//                                       ro section D_1,
//                                       ro section D_2,
//                                       block HEAP,
//                                       block STACKS,
//                                       last section FREEMEM };

//"DATAFLASH":place in DATA_FLASH_region
//                                     { ro section .dataflash* };

define movable block ROPI with alignment = 4, fixed order, static base CB
{
  ro object txm_module_preamble_rx63n.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base SB
{
  rw section .sbdata*,
  rw section .sbrel*,
  rw section __DLIB_PERTHREAD,
  block HEAP
};

place in ROM_region32   { block ROPI };
place in RAM_region16   { block RWPI };
```

#### <a name="building-modules-for-rx63-using-iar"></a><span data-ttu-id="11426-1029">IAR을 사용하는 RX63의 모듈 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-1029">Building Modules for RX63 using IAR</span></span>

<span data-ttu-id="11426-1030">예제 작업 영역이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="11426-1030">An example workspace is provided.</span></span> <span data-ttu-id="11426-1031">ThreadX 라이브러리, ThreadX 모듈 라이브러리, 데모 모듈 프로젝트 및 데모 모듈 관리자 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="11426-1031">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-rxrx635n-using-iar"></a><span data-ttu-id="11426-1032">IAR을 사용하는 RXRX635N의 스레드 확장 정의</span><span class="sxs-lookup"><span data-stu-id="11426-1032">Thread extension definition for RXRX635N using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;       \
                                VOID    *tx_thread_module_entry_info_ptr;     \
                                ULONG   tx_thread_module_current_user_mode;   \
                                ULONG   tx_thread_module_user_mode;           \
                                VOID    *tx_thread_module_kernel_stack_start; \
                                VOID    *tx_thread_module_kernel_stack_end;   \
                                ULONG   tx_thread_module_kernel_stack_size;   \
                                VOID    *tx_thread_module_stack_ptr;          \
                                VOID    *tx_thread_module_stack_start;        \
                                VOID    *tx_thread_module_stack_end;          \
                                ULONG   tx_thread_module_stack_size;          \
                                VOID    *tx_thread_module_reserved;           \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-rx63-using-iar"></a><span data-ttu-id="11426-1033">IAR을 사용하는 RX63의 모듈 관리자 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-1033">Building Module Manager for RX63 using IAR</span></span>

<span data-ttu-id="11426-1034">예제 작업 영역이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="11426-1034">An example workspace is provided.</span></span> <span data-ttu-id="11426-1035">ThreadX 라이브러리, ThreadX 모듈 라이브러리, 데모 모듈 프로젝트 및 데모 모듈 관리자 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="11426-1035">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-rx63-using-iar"></a><span data-ttu-id="11426-1036">IAR을 사용하는 RX63의 외부 메모리 사용 API에 대한 특성</span><span class="sxs-lookup"><span data-stu-id="11426-1036">Attributes for external memory enable API for RX63 using IAR</span></span>

| <span data-ttu-id="11426-1037">특성 매개 변수</span><span class="sxs-lookup"><span data-stu-id="11426-1037">Attribute Parameter</span></span> | <span data-ttu-id="11426-1038">의미</span><span class="sxs-lookup"><span data-stu-id="11426-1038">Meaning</span></span> |
|---|---|
| <span data-ttu-id="11426-1039">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span><span class="sxs-lookup"><span data-stu-id="11426-1039">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span></span> | <span data-ttu-id="11426-1040">코드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-1040">Execute code</span></span> |
| <span data-ttu-id="11426-1041">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="11426-1041">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="11426-1042">쓰기 액세스</span><span class="sxs-lookup"><span data-stu-id="11426-1042">Write access</span></span> |
| <span data-ttu-id="11426-1043">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span><span class="sxs-lookup"><span data-stu-id="11426-1043">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span></span> | <span data-ttu-id="11426-1044">읽기 액세스</span><span class="sxs-lookup"><span data-stu-id="11426-1044">Read access</span></span> |

## <a name="rx65n-processor"></a><span data-ttu-id="11426-1045">RX65N 프로세서</span><span class="sxs-lookup"><span data-stu-id="11426-1045">RX65N processor</span></span>

### <a name="rx65n-using-iar"></a><span data-ttu-id="11426-1046">IAR을 사용하는 RX65N</span><span class="sxs-lookup"><span data-stu-id="11426-1046">RX65N using IAR</span></span>

#### <a name="module-preamble-for-rx65n-using-iar"></a><span data-ttu-id="11426-1047">IAR을 사용하는 RX65N의 모듈 머리말</span><span class="sxs-lookup"><span data-stu-id="11426-1047">Module preamble for RX65N using IAR</span></span>

```c
    /* Alignment of 4 (16-byte) */
    SECTION .text:CODE (4)

    /* Define public symbols.  */
    PUBLIC __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    EXTERN _demo_module_start

    /* Define common external references.  */
    EXTERN  __txm_module_thread_shell_entry
    EXTERN  __txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        // Module ID
    DC32      0x5                                               // Module Major Version
    DC32      0x6                                               // Module Minor Version
    DC32      32                                                // Module Preamble Size in 32-bit words
    DC32      0x12345678                                        // Module ID (application defined)
    DC32      0x00000007                                        // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    DC32      __txm_module_thread_shell_entry - $               // Module Shell Entry Point
    DC32      _demo_module_start - $                            // Module Start Thread Entry Point
    DC32      0                                                 // Module Stop Thread Entry Point
    DC32      1                                                 // Module Start/Stop Thread Priority
    DC32      1024                                              // Module Start/Stop Thread Stack Size
    DC32      __txm_module_callback_request_thread_entry - $    // Module Callback Thread Entry
    DC32      1                                                 // Module Callback Thread Priority
    DC32      1024                                              // Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      // Module Code Size
    DC32      RWPI$$Length                                      // Module Data Size
    DC32      0                                                 // Reserved 0
    DC32      0                                                 // Reserved 1
    DC32      0                                                 // Reserved 2
    DC32      0                                                 // Reserved 3
    DC32      0                                                 // Reserved 4
    DC32      0                                                 // Reserved 5
    DC32      0                                                 // Reserved 6
    DC32      0                                                 // Reserved 7
    DC32      0                                                 // Reserved 8  
    DC32      0                                                 // Reserved 9
    DC32      0                                                 // Reserved 10
    DC32      0                                                 // Reserved 11
    DC32      0                                                 // Reserved 12
    DC32      0                                                 // Reserved 13
    DC32      0                                                 // Reserved 14
    DC32      0                                                 // Reserved 15

    END
```

#### <a name="module-properties-for-rx65n-using-iar"></a><span data-ttu-id="11426-1048">IAR을 사용하는 RX65N의 모듈 속성</span><span class="sxs-lookup"><span data-stu-id="11426-1048">Module properties for RX65N using IAR</span></span>

| <span data-ttu-id="11426-1049">bit</span><span class="sxs-lookup"><span data-stu-id="11426-1049">Bit</span></span> | <span data-ttu-id="11426-1050">값</span><span class="sxs-lookup"><span data-stu-id="11426-1050">Value</span></span> | <span data-ttu-id="11426-1051">의미</span><span class="sxs-lookup"><span data-stu-id="11426-1051">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="11426-1052">0</span><span class="sxs-lookup"><span data-stu-id="11426-1052">0</span></span> | <span data-ttu-id="11426-1053">0</span><span class="sxs-lookup"><span data-stu-id="11426-1053">0</span></span><br /><span data-ttu-id="11426-1054">1</span><span class="sxs-lookup"><span data-stu-id="11426-1054">1</span></span> | <span data-ttu-id="11426-1055">권한 있는 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-1055">Privileged mode execution</span></span><br /><span data-ttu-id="11426-1056">사용자 모드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-1056">User mode execution</span></span> |
| <span data-ttu-id="11426-1057">1</span><span class="sxs-lookup"><span data-stu-id="11426-1057">1</span></span> | <span data-ttu-id="11426-1058">0</span><span class="sxs-lookup"><span data-stu-id="11426-1058">0</span></span><br /><span data-ttu-id="11426-1059">1</span><span class="sxs-lookup"><span data-stu-id="11426-1059">1</span></span> | <span data-ttu-id="11426-1060">MPU 보호 없음</span><span class="sxs-lookup"><span data-stu-id="11426-1060">No MPU protection</span></span><br /><span data-ttu-id="11426-1061">MPU 보호(사용자 모드가 선택되어 있어야 함)</span><span class="sxs-lookup"><span data-stu-id="11426-1061">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="11426-1062">2</span><span class="sxs-lookup"><span data-stu-id="11426-1062">2</span></span> | <span data-ttu-id="11426-1063">0</span><span class="sxs-lookup"><span data-stu-id="11426-1063">0</span></span><br /><span data-ttu-id="11426-1064">1</span><span class="sxs-lookup"><span data-stu-id="11426-1064">1</span></span> | <span data-ttu-id="11426-1065">공유/외부 메모리 액세스 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="11426-1065">Disable shared/external memory access</span></span><br /><span data-ttu-id="11426-1066">공유/외부 메모리 액세스 사용</span><span class="sxs-lookup"><span data-stu-id="11426-1066">Enable shared/external memory access</span></span> |
| <span data-ttu-id="11426-1067">[23-3]</span><span class="sxs-lookup"><span data-stu-id="11426-1067">[23-3]</span></span> | <span data-ttu-id="11426-1068">0</span><span class="sxs-lookup"><span data-stu-id="11426-1068">0</span></span> | <span data-ttu-id="11426-1069">예약됨</span><span class="sxs-lookup"><span data-stu-id="11426-1069">Reserved</span></span>
| <span data-ttu-id="11426-1070">[31-24]</span><span class="sxs-lookup"><span data-stu-id="11426-1070">[31-24]</span></span> | <br /><span data-ttu-id="11426-1071">0x00</span><span class="sxs-lookup"><span data-stu-id="11426-1071">0x00</span></span><br /><span data-ttu-id="11426-1072">0x02</span><span class="sxs-lookup"><span data-stu-id="11426-1072">0x02</span></span> | <span data-ttu-id="11426-1073">**컴파일러 ID**</span><span class="sxs-lookup"><span data-stu-id="11426-1073">**Compiler ID**</span></span><br /><span data-ttu-id="11426-1074">IAR</span><span class="sxs-lookup"><span data-stu-id="11426-1074">IAR</span></span><br /><span data-ttu-id="11426-1075">GNU</span><span class="sxs-lookup"><span data-stu-id="11426-1075">GNU</span></span> |

#### <a name="module-linker-for-rx65n-using-iar"></a><span data-ttu-id="11426-1076">IAR을 사용하는 RX65N의 모듈 링커</span><span class="sxs-lookup"><span data-stu-id="11426-1076">Module linker for RX65N using IAR</span></span>

```c
//-----------------------------------------------------------------------------
// ILINK command file template for the Renesas RX microcontroller R5F565N
//-----------------------------------------------------------------------------
define exported symbol __link_file_version_4 = 1;

define memory mem with size = 4G;

// ID Code Protection
define exported symbol __ID_BYTES_1_4   = 0xFFFFFFFF;
define exported symbol __ID_BYTES_5_8   = 0xFFFFFFFF;
define exported symbol __ID_BYTES_9_12  = 0xFFFFFFFF;
define exported symbol __ID_BYTES_13_16 = 0xFFFFFFFF;

// Endian Select Register (MDE)
// Choose between Little endian=0xFFFFFFFF or Big endian=0xFFFFFFF8
define exported symbol __MDES           = 0xFFFFFFFF;

// Option Function Select Register 0 (OFS0)
define exported symbol __OFS0           = 0xFFFFFFFF;

// Option Function Select Register 1 (OFS1)
define exported symbol __OFS1           = 0xFFFFFFFF;

//define region ROM_region16 = mem:[from 0xFFFF8000 to 0xFFFFFFFF];
define region RAM_region16 = mem:[from 0x00010000 to 0x00017FFF];
//define region ROM_region24 = mem:[from 0xFFF00000 to 0xFFFFFFFF];
//define region RAM_region24 = mem:[from 0x00000004 to 0x0001FFFF];
define region ROM_region32 = mem:[from 0xFFF10400 to 0xFFFFFFFF];
//define region RAM_region32 = mem:[from 0x00000004 to 0x0001FFFF];
//define region DATA_FLASH_region = mem:[from 0x00100000 to 0x00107FFF];

initialize by copy { rw, ro section D, ro section D_1, ro section D_2 };
do not initialize  { section .*.noinit };

define block HEAP     with alignment = 4, size = _HEAP_SIZE { };
//define block USTACK   with alignment = 4, size = _USTACK_SIZE { };
//define block ISTACK   with alignment = 4, size = _ISTACK_SIZE { };

//define block STACKS with fixed order { block ISTACK,
//                                       block USTACK };

//place at address mem:0xFFFFFF80 { ro section .nmivec };
//"ROM16":place in ROM_region16        { ro section .code16*,
//                                       ro section .data16* };
//"RAM16":place in RAM_region16        { rw section .data16*,
//                                       rw section __DLIB_PERTHREAD };
//"ROM24":place in ROM_region24        { ro section .code24*,
//                                       ro section .data24* };
//"RAM24":place in RAM_region24        { rw section .data24* };
//"ROM32":place in ROM_region32        { ro };
//"RAM32":place in RAM_region32        { rw,
//                                       ro section D,
//                                       ro section D_1,
//                                       ro section D_2,
//                                       block HEAP,
//                                       block STACKS,
//                                       last section FREEMEM };

//"DATAFLASH":place in DATA_FLASH_region
//                                     { ro section .dataflash* };

define movable block ROPI with alignment = 4, fixed order, static base CB
{
  ro object txm_module_preamble_rx65n.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base SB
{
  rw section .sbdata*,
  rw section .sbrel*,
  rw section __DLIB_PERTHREAD,
  block HEAP
};

place in ROM_region32   { block ROPI };
place in RAM_region16   { block RWPI };
```

#### <a name="building-modules-for-rx65n-using-iar"></a><span data-ttu-id="11426-1077">IAR을 사용하는 RX65N의 모듈 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-1077">Building Modules for RX65N using IAR</span></span>

<span data-ttu-id="11426-1078">예제 작업 영역이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="11426-1078">An example workspace is provided.</span></span> <span data-ttu-id="11426-1079">ThreadX 라이브러리, ThreadX 모듈 라이브러리, 데모 모듈 프로젝트 및 데모 모듈 관리자 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="11426-1079">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-rx65n-using-iar"></a><span data-ttu-id="11426-1080">IAR을 사용하는 RX65N의 스레드 확장 정의</span><span class="sxs-lookup"><span data-stu-id="11426-1080">Thread extension definition for RX65N using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-rx65n-using-iar"></a><span data-ttu-id="11426-1081">IAR을 사용하는 RX65N의 모듈 관리자 빌드</span><span class="sxs-lookup"><span data-stu-id="11426-1081">Building Module Manager for RX65N using IAR</span></span>

<span data-ttu-id="11426-1082">예제 작업 영역이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="11426-1082">An example workspace is provided.</span></span> <span data-ttu-id="11426-1083">ThreadX 라이브러리, ThreadX 모듈 라이브러리, 데모 모듈 프로젝트 및 데모 모듈 관리자 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="11426-1083">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-rx65n-using-iar"></a><span data-ttu-id="11426-1084">IAR을 사용하는 RX65N의 외부 메모리 사용 API에 대한 특성</span><span class="sxs-lookup"><span data-stu-id="11426-1084">Attributes for external memory enable API for RX65N using IAR</span></span>

| <span data-ttu-id="11426-1085">특성 매개 변수</span><span class="sxs-lookup"><span data-stu-id="11426-1085">Attribute Parameter</span></span> | <span data-ttu-id="11426-1086">의미</span><span class="sxs-lookup"><span data-stu-id="11426-1086">Meaning</span></span> |
|---|---|
| <span data-ttu-id="11426-1087">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span><span class="sxs-lookup"><span data-stu-id="11426-1087">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span></span> | <span data-ttu-id="11426-1088">코드 실행</span><span class="sxs-lookup"><span data-stu-id="11426-1088">Execute code</span></span> |
| <span data-ttu-id="11426-1089">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="11426-1089">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="11426-1090">쓰기 액세스</span><span class="sxs-lookup"><span data-stu-id="11426-1090">Write access</span></span> |
| <span data-ttu-id="11426-1091">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span><span class="sxs-lookup"><span data-stu-id="11426-1091">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span></span> | <span data-ttu-id="11426-1092">읽기 액세스</span><span class="sxs-lookup"><span data-stu-id="11426-1092">Read access</span></span> |
