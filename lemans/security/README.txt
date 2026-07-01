1. Security assets for U-Boot SPL signing — the following file is present here:

    swiv_build_utility.py            SWIV segment annotation tool (Stage 1 signing)

Used by the spl target (SWIV annotation + qtestsign signing):

    python3 lemans/security/swiv_build_utility.py \
        .output/spl/u-boot-spl-swiv.elf \
        .output/spl/u-boot-spl.elf \
        lemans

    <path_to_qtestsign>/qtestsign -v6 tz \
        -o .output/spl/u-boot-spl.mbn \
        .output/spl/u-boot-spl-swiv.elf

The resulting u-boot-spl.mbn is copied to lemans/output/tz.mbn (the tz
partition image). Signing is done locally with qtestsign (open-source — no
QTI CASS / security profile required).
