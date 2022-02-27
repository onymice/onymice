- 👋 Hi, I’m @onymice
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
onymice/onymice is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
 3  binr/blob/version.c 

@@ -1,6 +1,7 @@
 /* copyright 2015-2016 radare2 by pancake */
 /* copyright 2015-2017 radare2 by pancake */

 #include <r_userconf.h>
 #include <r_util.h>

 #ifndef R2_GITTAP
 #define R2_GITTAP ""
    32  binr/rasm2/rasm2.c 

@@ -1,14 +1,14 @@
 /* radare - LGPL - Copyright 2009-2016 - pancake, nibble, maijin */

 #include <stdio.h>
 #include <string.h>
 #include "../blob/version.c"
 #include <getopt.c> /* getopt.h is not portable :D */
 #include <r_types.h>
 #include <r_asm.h>
 #include <r_anal.h>
 #include <r_util.h>
 #include <r_asm.h>
 #include <r_lib.h>
 #include "../blob/version.c"
 #include <r_types.h>
 #include <r_util.h>
 #include <stdio.h>
 #include <string.h>

 static RLib *l = NULL;
 static RAsm *a = NULL;
 @@ -28,7 +28,7 @@ static int show_analinfo(const char *arg, ut64 offset) {
 	if (json) {
 		printf ("[");
 	}
 	for (ret = 0; ret < len; ) {
 	for (ret = 0; ret < len;) {
 		aop.size = 0;
 		if (r_anal_op (anal, &aop, offset, buf + ret, len - ret) > 0) {
 			//printf ("%s\n", R_STRBUF_SAFEGET (&aop.esil));
 @@ -105,11 +105,11 @@ static void rasm2_list(RAsm *la, const char *arch) {
 				const char *str_bits = "32, 64";
 				const char *license = "GPL";
 				printf ("\"%s\":{\"bits\":[%s],\"license\":\"%s\",\"description\":\"%s\",\"features\":\"%s\"}%s",
 						h->name, str_bits, license, h->desc, feat, iter->n? ",": "");
 					h->name, str_bits, license, h->desc, feat, iter->n? ",": "");
 			} else {
 				printf ("%s%s  %-9s  %-11s %-7s %s\n",
 						feat, feat2, bits, h->name,
 						h->license? h->license: "unknown", h->desc);
 					feat, feat2, bits, h->name,
 					h->license? h->license: "unknown", h->desc);
 			}
 		}
 	}
 @@ -212,14 +212,12 @@ static int rasm_show_help(int v) {
 			" If '-l' value is greater than output length, output is padded with nops\n"
 			" If the last argument is '-' reads from stdin\n");
 		printf ("Environment:\n"
 		" RASM2_NOPLUGINS  do not load shared plugins (speedup loading)\n"
 		" R_DEBUG          if defined, show error messages and crash signal\n"
 		"");
 			" RASM2_NOPLUGINS  do not load shared plugins (speedup loading)\n"
 			" R_DEBUG          if defined, show error messages and crash signal\n"
 			"");
 	}
 	if (v == 2) {
 		printf (
 		"Supported Assembler directives:\n"
 		);
 		printf ("Supported Assembler directives:\n");
 		r_asm_list_directives ();
 	}
 	return 0;
 @@ -458,7 +456,7 @@ int main (int argc, char *argv[]) {
 			filters = optarg;
 			break;
 		case 'h':
 			help ++;
 			help++;
 		case 'i':
 			skip = r_num_math (NULL, optarg);
 			break;
