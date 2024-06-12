const SECTION_CUSTOM = 0;
const SECTION_TYPE = 1;
const SECTION_IMPORT = 2;
const SECTION_FUNCTION = 3;
const SECTION_TABLE = 4;
const SECTION_MEMORY = 5;
const SECTION_GLOBAL = 6;
const SECTION_EXPORT = 7;
const SECTION_START = 8;
const SECTION_ELEMENT = 9;
const SECTION_CODE = 10;
const SECTION_DATA = 11;
const SECTION_DATACOUNT = 12;
const MAX_SECTION_ID = 12;

const KIND_FUNC = 0;
const KIND_TABLE = 1;
const KIND_MEMORY = 2;
const KIND_GLOBAL = 3;

const kindStr = { func: KIND_FUNC, table: KIND_TABLE, memory: KIND_MEMORY, global: KIND_GLOBAL };

const convertKind = function(string) {
  const kindVal = kindStr[string];
  if (typeof kindVal === "undefined") {
    throw new Error("Invalid kind " + string);
  }
  return kindVal;
};

const VALUE_TYPE_I32 = 127;
const VALUE_TYPE_I64 = 126;
const VALUE_TYPE_F32 = 125;
const VALUE_TYPE_F64 = 124;
const VALUE_TYPE_V128 = 123;
const VALUE_TYPE_ANYFUNC = 112;
const VALUE_TYPE_FUNC = 96;
const VALUE_TYPE_BLOCK = 64;

const valueTypeStr = {
  i32: VALUE_TYPE_I32,
  i64: VALUE_TYPE_I64,
  f32: VALUE_TYPE_F32,
  f64: VALUE_TYPE_F64,
  v128: VALUE_TYPE_V128,
  anyfunc: VALUE_TYPE_ANYFUNC,
  func: VALUE_TYPE_FUNC,
  block: VALUE_TYPE_BLOCK
};

const convertValueType = function(string) {
  const typeVal = valueTypeStr[string];
  if (typeof typeVal === "undefined") {
    throw new Error("Invalid value type " + string);
  }
  return typeVal;
};

const ELEM_SEG_FLAG_NONE = 0;
const ELEM_SEG_FLAG_PASSIVE = 1;
const ELEM_SEG_FLAG_EXPLICIT_INDEX = 2;
const ELEM_SEG_FLAG_DECLARED = 3;
const ELEM_SEG_FLAG_USE_ELEM_EXPRS = 4;

const OP_UNREACHABLE = 0;
const OP_NOP = 1;
const OP_BLOCK = 2;
const OP_LOOP = 3;
const OP_IF = 4;
const OP_ELSE = 5;
const OP_TRY = 6;
const OP_CATCH = 7;
const OP_THROW = 8;
const OP_RETHROW = 9;
const OP_END = 11;
const OP_BR = 12;
const OP_BR_IF = 13;
const OP_BR_TABLE = 14;
const OP_RETURN = 15;
const OP_CALL = 16;
const OP_CALL_INDIRECT = 17;
const OP_DROP = 26;
const OP_SELECT = 27;
const OP_GET_LOCAL = 32;
const OP_SET_LOCAL = 33;
const OP_TEE_LOCAL = 34;
const OP_GET_GLOBAL = 35;
const OP_SET_GLOBAL = 36;
const OP_TABLE_GET = 37;
const OP_TABLE_SET = 38;
const OP_I32_LOAD = 40;
const OP_I64_LOAD = 41;
const OP_F32_LOAD = 42;
const OP_F64_LOAD = 43;
const OP_I32_LOAD8_S = 44;
const OP_I32_LOAD8_U = 45;
const OP_I32_LOAD16_S = 46;
const OP_I32_LOAD16_U = 47;
const OP_I64_LOAD8_S = 48;
const OP_I64_LOAD8_U = 49;
const OP_I64_LOAD16_S = 50;
const OP_I64_LOAD16_U = 51;
const OP_I64_LOAD32_S = 52;
const OP_I64_LOAD32_U = 53;
const OP_I32_STORE = 54;
const OP_I64_STORE = 55;
const OP_F32_STORE = 56;
const OP_F64_STORE = 57;
const OP_I32_STORE8 = 58;
const OP_I32_STORE16 = 59;
const OP_I64_STORE8 = 60;
const OP_I64_STORE16 = 61;
const OP_I64_STORE32 = 62;
const OP_MEMORY_SIZE = 63;
const OP_MEMORY_GROW = 64;
const OP_I32_CONST = 65;
const OP_I64_CONST = 66;
const OP_F32_CONST = 67;
const OP_F64_CONST = 68;
const OP_I32_EQZ = 69;
const OP_I32_EQ = 70;
const OP_I32_NE = 71;
const OP_I32_LT_S = 72;
const OP_I32_LT_U = 73;
const OP_I32_GT_S = 74;
const OP_I32_GT_U = 75;
const OP_I32_LE_S = 76;
const OP_I32_LE_U = 77;
const OP_I32_GE_S = 78;
const OP_I32_GE_U = 79;
const OP_I64_EQZ = 80;
const OP_I64_EQ = 81;
const OP_I64_NE = 82;
const OP_I64_LT_S = 83;
const OP_I64_LT_U = 84;
const OP_I64_GT_S = 85;
const OP_I64_GT_U = 86;
const OP_I64_LE_S = 87;
const OP_I64_LE_U = 88;
const OP_I64_GE_S = 89;
const OP_I64_GE_U = 90;
const OP_F32_EQ = 91;
const OP_F32_NE = 92;
const OP_F32_LT = 93;
const OP_F32_GT = 94;
const OP_F32_LE = 95;
const OP_F32_GE = 96;
const OP_F64_EQ = 97;
const OP_F64_NE = 98;
const OP_F64_LT = 99;
const OP_F64_GT = 100;
const OP_F64_LE = 101;
const OP_F64_GE = 102;
const OP_I32_CLZ = 103;
const OP_I32_CTZ = 104;
const OP_I32_POPCNT = 105;
const OP_I32_ADD = 106;
const OP_I32_SUB = 107;
const OP_I32_MUL = 108;
const OP_I32_DIV_S = 109;
const OP_I32_DIV_U = 110;
const OP_I32_REM_S = 111;
const OP_I32_REM_U = 112;
const OP_I32_AND = 113;
const OP_I32_OR = 114;
const OP_I32_XOR = 115;
const OP_I32_SHL = 116;
const OP_I32_SHR_S = 117;
const OP_I32_SHR_U = 118;
const OP_I32_ROTL = 119;
const OP_I32_ROTR = 120;
const OP_I64_CLZ = 121;
const OP_I64_CTZ = 122;
const OP_I64_POPCNT = 123;
const OP_I64_ADD = 124;
const OP_I64_SUB = 125;
const OP_I64_MUL = 126;
const OP_I64_DIV_S = 127;
const OP_I64_DIV_U = 128;
const OP_I64_REM_S = 129;
const OP_I64_REM_U = 130;
const OP_I64_AND = 131;
const OP_I64_OR = 132;
const OP_I64_XOR = 133;
const OP_I64_SHL = 134;
const OP_I64_SHR_S = 135;
const OP_I64_SHR_U = 136;
const OP_I64_ROTL = 137;
const OP_I64_ROTR = 138;
const OP_F32_ABS = 139;
const OP_F32_NEG = 140;
const OP_F32_CEIL = 141;
const OP_F32_FLOOR = 142;
const OP_F32_TRUNC = 143;
const OP_F32_NEAREST = 144;
const OP_F32_SQRT = 145;
const OP_F32_ADD = 146;
const OP_F32_SUB = 147;
const OP_F32_MUL = 148;
const OP_F32_DIV = 149;
const OP_F32_MIN = 150;
const OP_F32_MAX = 151;
const OP_F32_COPYSIGN = 152;
const OP_F64_ABS = 153;
const OP_F64_NEG = 154;
const OP_F64_CEIL = 155;
const OP_F64_FLOOR = 156;
const OP_F64_TRUNC = 157;
const OP_F64_NEAREST = 158;
const OP_F64_SQRT = 159;
const OP_F64_ADD = 160;
const OP_F64_SUB = 161;
const OP_F64_MUL = 162;
const OP_F64_DIV = 163;
const OP_F64_MIN = 164;
const OP_F64_MAX = 165;
const OP_F64_COPYSIGN = 166;
const OP_I32_WRAP_I64 = 167;
const OP_I32_TRUNC_S_F32 = 168;
const OP_I32_TRUNC_U_F32 = 169;
const OP_I32_TRUNC_S_F64 = 170;
const OP_I32_TRUNC_U_F64 = 171;
const OP_I64_EXTEND_S_I32 = 172;
const OP_I64_EXTEND_U_I32 = 173;
const OP_I64_TRUNC_S_F32 = 174;
const OP_I64_TRUNC_U_F32 = 175;
const OP_I64_TRUNC_S_F64 = 176;
const OP_I64_TRUNC_U_F64 = 177;
const OP_F32_CONVERT_S_I32 = 178;
const OP_F32_CONVERT_U_I32 = 179;
const OP_F32_CONVERT_S_I64 = 180;
const OP_F32_CONVERT_U_I64 = 181;
const OP_F32_DEMOTE_F64 = 182;
const OP_F64_CONVERT_S_I32 = 183;
const OP_F64_CONVERT_U_I32 = 184;
const OP_F64_CONVERT_S_I64 = 185;
const OP_F64_CONVERT_U_I64 = 186;
const OP_F64_PROMOTE_F32 = 187;
const OP_I32_REINTERPRET_F32 = 188;
const OP_I64_REINTERPRET_F64 = 189;
const OP_F32_REINTERPRET_I32 = 190;
const OP_F64_REINTERPRET_I64 = 191;
const OP_I32_EXTEND8_S = 192;
const OP_I32_EXTEND16_S = 193;
const OP_I64_EXTEND8_S = 194;
const OP_I64_EXTEND16_S = 195;
const OP_I64_EXTEND32_S = 196;
const OP_REF_NULL = 208;
const OP_REF_IS_NULL = 209;
const OP_REF_FUNC = 210;
const OP_REF_AS_NON_NULL = 211;
const OP_BR_ON_NULL = 212;
const OP_REF_EQ = 213;
const OP_BR_ON_NON_NULL = 214;
const OP_MISC = 252;
const OP_SIMD = 253;
const OP_ATOMIC = 254;

const ARG_I32_TRUNC_SAT_F32_S = 0;
const ARG_I32_TRUNC_SAT_F32_U = 1;
const ARG_I32_TRUNC_SAT_F64_S = 2;
const ARG_I32_TRUNC_SAT_F64_U = 3;
const ARG_I64_TRUNC_SAT_F32_S = 4;
const ARG_I64_TRUNC_SAT_F32_U = 5;
const ARG_I64_TRUNC_SAT_F64_S = 6;
const ARG_I64_TRUNC_SAT_F64_U = 7;
const ARG_MEMORY_INIT = 8;
const ARG_DATA_DROP = 9;
const ARG_MEMORY_COPY = 10;
const ARG_MEMORY_FILL = 11;
const ARG_TABLE_INIT = 12;
const ARG_ELEM_DROP = 13;
const ARG_TABLE_COPY = 14;
const ARG_TABLE_GROW = 15;

const SIMD_V128_LOAD = 0;
const SIMD_V128_LOAD8X8_S = 1;
const SIMD_V128_LOAD8X8_U = 2;
const SIMD_V128_LOAD16X4_S = 3;
const SIMD_V128_LOAD16X4_U = 4;
const SIMD_V128_LOAD32X2_S = 5;
const SIMD_V128_LOAD32X2_U = 6;
const SIMD_V128_LOAD8_SPLAT = 7;
const SIMD_V128_LOAD16_SPLAT = 8;
const SIMD_V128_LOAD32_SPLAT = 9;
const SIMD_V128_LOAD64_SPLAT = 10;
const SIMD_V128_STORE = 11;
const SIMD_V128_CONST = 12;
const SIMD_I8X16_SHUFFLE = 13;
const SIMD_I8X16_SWIZZLE = 14;
const SIMD_I8X16_SPLAT = 15;
const SIMD_I16X8_SPLAT = 16;
const SIMD_I32X4_SPLAT = 17;
const SIMD_I64X2_SPLAT = 18;
const SIMD_F32X4_SPLAT = 19;
const SIMD_F64X2_SPLAT = 20;
const SIMD_I8X16_EXTRACT_LANE_S = 21;
const SIMD_I8X16_EXTRACT_LANE_U = 22;
const SIMD_I8X16_REPLACE_LANE = 23;
const SIMD_I16X8_EXTRACT_LANE_S = 24;
const SIMD_I16X8_EXTRACT_LANE_U = 25;
const SIMD_I16X8_REPLACE_LANE = 26;
const SIMD_I32X4_EXTRACT_LANE = 27;
const SIMD_I32X4_REPLACE_LANE = 28;
const SIMD_I64X2_EXTRACT_LANE = 29;
const SIMD_I64X2_REPLACE_LANE = 30;
const SIMD_F32X4_EXTRACT_LANE = 31;
const SIMD_F32X4_REPLACE_LANE = 32;
const SIMD_F64X2_EXTRACT_LANE = 33;
const SIMD_F64X2_REPLACE_LANE = 34;
const SIMD_I8X16_EQ = 35;
const SIMD_I8X16_NE = 36;
const SIMD_I8X16_LT_S = 37;
const SIMD_I8X16_LT_U = 38;
const SIMD_I8X16_GT_S = 39;
const SIMD_I8X16_GT_U = 40;
const SIMD_I8X16_LE_S = 41;
const SIMD_I8X16_LE_U = 42;
const SIMD_I8X16_GE_S = 43;
const SIMD_I8X16_GE_U = 44;
const SIMD_I16X8_EQ = 45;
const SIMD_I16X8_NE = 46;
const SIMD_I16X8_LT_S = 47;
const SIMD_I16X8_LT_U = 48;
const SIMD_I16X8_GT_S = 49;
const SIMD_I16X8_GT_U = 50;
const SIMD_I16X8_LE_S = 51;
const SIMD_I16X8_LE_U = 52;
const SIMD_I16X8_GE_S = 53;
const SIMD_I16X8_GE_U = 54;
const SIMD_I32X4_EQ = 55;
const SIMD_I32X4_NE = 56;
const SIMD_I32X4_LT_S = 57;
const SIMD_I32X4_LT_U = 58;
const SIMD_I32X4_GT_S = 59;
const SIMD_I32X4_GT_U = 60;
const SIMD_I32X4_LE_S = 61;
const SIMD_I32X4_LE_U = 62;
const SIMD_I32X4_GE_S = 63;
const SIMD_I32X4_GE_U = 64;
const SIMD_F32X4_EQ = 65;
const SIMD_F32X4_NE = 66;
const SIMD_F32X4_LT = 67;
const SIMD_F32X4_GT = 68;
const SIMD_F32X4_LE = 69;
const SIMD_F32X4_GE = 70;
const SIMD_F64X2_EQ = 71;
const SIMD_F64X2_NE = 72;
const SIMD_F64X2_LT = 73;
const SIMD_F64X2_GT = 74;
const SIMD_F64X2_LE = 75;
const SIMD_F64X2_GE = 76;
const SIMD_V128_NOT = 77;
const SIMD_V128_AND = 78;
const SIMD_V128_ANDNOT = 79;
const SIMD_V128_OR = 80;
const SIMD_V128_XOR = 81;
const SIMD_V128_BITSELECT = 82;
const SIMD_I8X16_ABS = 96;
const SIMD_I8X16_NEG = 97;
const SIMD_I8X16_ALL_TRUE = 99;
const SIMD_I8X16_BITMASK = 100;
const SIMD_I8X16_NARROW_I16X8_S = 101;
const SIMD_I8X16_NARROW_I16X8_U = 102;
const SIMD_I8X16_SHL = 107;
const SIMD_I8X16_SHR_S = 108;
const SIMD_I8X16_SHR_U = 109;
const SIMD_I8X16_ADD = 110;
const SIMD_I8X16_ADD_SAT_S = 111;
const SIMD_I8X16_ADD_SAT_U = 112;
const SIMD_I8X16_SUB = 113;
const SIMD_I8X16_SUB_SAT_S = 114;
const SIMD_I8X16_SUB_SAT_U = 115;
const SIMD_I8X16_MIN_S = 118;
const SIMD_I8X16_MIN_U = 119;
const SIMD_I8X16_MAX_S = 120;
const SIMD_I8X16_MAX_U = 121;
const SIMD_I8X16_AVGR_U = 123;
const SIMD_I16X8_ABS = 128;
const SIMD_I16X8_NEG = 129;
const SIMD_I16X8_ALL_TRUE = 131;
const SIMD_I16X8_BITMASK = 132;
const SIMD_I16X8_NARROW_I32X4_S = 133;
const SIMD_I16X8_NARROW_I32X4_U = 134;
const SIMD_I16X8_EXTEND_LOW_I8X16_S = 135;
const SIMD_I16X8_EXTEND_HIGH_I8X16_S = 136;
const SIMD_I16X8_EXTEND_LOW_I8X16_U = 137;
const SIMD_I16X8_EXTEND_HIGH_I8X16_U = 138;
const SIMD_I16X8_SHL = 139;
const SIMD_I16X8_SHR_S = 140;
const SIMD_I16X8_SHR_U = 141;
const SIMD_I16X8_ADD = 142;
const SIMD_I16X8_ADD_SAT_S = 143;
const SIMD_I16X8_ADD_SAT_U = 144;
const SIMD_I16X8_SUB = 145;
const SIMD_I16X8_SUB_SAT_S = 146;
const SIMD_I16X8_SUB_SAT_U = 147;
const SIMD_I16X8_MUL = 149;
const SIMD_I16X8_MIN_S = 150;
const SIMD_I16X8_MIN_U = 151;
const SIMD_I16X8_MAX_S = 152;
const SIMD_I16X8_MAX_U = 153;
const SIMD_I16X8_AVGR_U = 155;
const SIMD_I32X4_ABS = 160;
const SIMD_I32X4_NEG = 161;
const SIMD_I32X4_ALL_TRUE = 163;
const SIMD_I32X4_BITMASK = 164;
const SIMD_I32X4_EXTEND_LOW_I16X8_S = 167;
const SIMD_I32X4_EXTEND_HIGH_I16X8_S = 168;
const SIMD_I32X4_EXTEND_LOW_I16X8_U = 169;
const SIMD_I32X4_EXTEND_HIGH_I16X8_U = 170;
const SIMD_I32X4_SHL = 171;
const SIMD_I32X4_SHR_S = 172;
const SIMD_I32X4_SHR_U = 173;
const SIMD_I32X4_ADD = 174;
const SIMD_I32X4_SUB = 177;
const SIMD_I32X4_MUL = 181;
const SIMD_I32X4_MIN_S = 182;
const SIMD_I32X4_MIN_U = 183;
const SIMD_I32X4_MAX_S = 184;
const SIMD_I32X4_MAX_U = 185;
const SIMD_I32X4_DOT_I16X8_S = 186;
const SIMD_I64X2_ABS = 192;
const SIMD_I64X2_NEG = 193;
const SIMD_I64X2_BITMASK = 196;
const SIMD_I64X2_EXTEND_LOW_I32X4_S = 199;
const SIMD_I64X2_EXTEND_HIGH_I32X4_S = 200;
const SIMD_I64X2_EXTEND_LOW_I32X4_U = 201;
const SIMD_I64X2_EXTEND_HIGH_I32X4_U = 202;
const SIMD_I64X2_SHL = 203;
const SIMD_I64X2_SHR_S = 204;
const SIMD_I64X2_SHR_U = 205;
const SIMD_I64X2_ADD = 206;
const SIMD_I64X2_SUB = 209;
const SIMD_I64X2_MUL = 213;
const SIMD_F32X4_CEIL = 103;
const SIMD_F32X4_FLOOR = 104;
const SIMD_F32X4_TRUNC = 105;
const SIMD_F32X4_NEAREST = 106;
const SIMD_F64X2_CEIL = 116;
const SIMD_F64X2_FLOOR = 117;
const SIMD_F64X2_TRUNC = 122;
const SIMD_F64X2_NEAREST = 148;
const SIMD_F32X4_ABS = 224;
const SIMD_F32X4_NEG = 225;
const SIMD_F32X4_SQRT = 227;
const SIMD_F32X4_ADD = 228;
const SIMD_F32X4_SUB = 229;
const SIMD_F32X4_MUL = 230;
const SIMD_F32X4_DIV = 231;
const SIMD_F32X4_MIN = 232;
const SIMD_F32X4_MAX = 233;
const SIMD_F32X4_PMIN = 234;
const SIMD_F32X4_PMAX = 235;
const SIMD_F64X2_ABS = 236;
const SIMD_F64X2_NEG = 237;
const SIMD_F64X2_SQRT = 239;
const SIMD_F64X2_ADD = 240;
const SIMD_F64X2_SUB = 241;
const SIMD_F64X2_MUL = 242;
const SIMD_F64X2_DIV = 243;
const SIMD_F64X2_MIN = 244;
const SIMD_F64X2_MAX = 245;
const SIMD_F64X2_PMIN = 246;
const SIMD_F64X2_PMAX = 247;
const SIMD_I32X4_TRUNC_SAT_F32X4_S = 248;
const SIMD_I32X4_TRUNC_SAT_F32X4_U = 249;
const SIMD_F32X4_CONVERT_I32X4_S = 250;
const SIMD_F32X4_CONVERT_I32X4_U = 251;
const SIMD_V128_LOAD32_ZERO = 92;
const SIMD_V128_LOAD64_ZERO = 93;
const SIMD_I16X8_EXTMUL_LOW_I8X16_S = 156;
const SIMD_I16X8_EXTMUL_HIGH_I8X16_S = 157;
const SIMD_I16X8_EXTMUL_LOW_I8X16_U = 158;
const SIMD_I16X8_EXTMUL_HIGH_I8X16_U = 159;
const SIMD_I32X4_EXTMUL_LOW_I16X8_S = 188;
const SIMD_I32X4_EXTMUL_HIGH_I16X8_S = 189;
const SIMD_I32X4_EXTMUL_LOW_I16X8_U = 190;
const SIMD_I32X4_EXTMUL_HIGH_I16X8_U = 191;
const SIMD_I64X2_EXTMUL_LOW_I32X4_S = 220;
const SIMD_I64X2_EXTMUL_HIGH_I32X4_S = 221;
const SIMD_I64X2_EXTMUL_LOW_I32X4_U = 222;
const SIMD_I64X2_EXTMUL_HIGH_I32X4_U = 223;
const SIMD_I16X8_Q15MULR_SAT_S = 130;
const SIMD_V128_ANY_TRUE = 83;
const SIMD_V128_LOAD8_LANE = 84;
const SIMD_V128_LOAD16_LANE = 85;
const SIMD_V128_LOAD32_LANE = 86;
const SIMD_V128_LOAD64_LANE = 87;
const SIMD_V128_STORE8_LANE = 88;
const SIMD_V128_STORE16_LANE = 89;
const SIMD_V128_STORE32_LANE = 90;
const SIMD_V128_STORE64_LANE = 91;
const SIMD_I64X2_EQ = 214;
const SIMD_I64X2_NE = 215;
const SIMD_I64X2_LT_S = 216;
const SIMD_I64X2_GT_S = 217;
const SIMD_I64X2_LE_S = 218;
const SIMD_I64X2_GE_S = 219;
const SIMD_I64X2_ALL_TRUE = 195;
const SIMD_F64X2_CONVERT_LOW_I32X4_S = 254;
const SIMD_F64X2_CONVERT_LOW_I32X4_U = 255;
const SIMD_I32X4_TRUNC_SAT_F64X2_S_ZERO = 252;
const SIMD_I32X4_TRUNC_SAT_F64X2_U_ZERO = 253;
const SIMD_F32X4_DEMOTE_F64X2_ZERO = 94;
const SIMD_F64X2_PROMOTE_LOW_F32X4 = 95;
const SIMD_I8X16_POPCNT = 98;
const SIMD_I16X8_EXTADD_PAIRWISE_I8X16_S = 124;
const SIMD_I16X8_EXTADD_PAIRWISE_I8X16_U = 125;
const SIMD_I32X4_EXTADD_PAIRWISE_I16X8_S = 126;
const SIMD_I32X4_EXTADD_PAIRWISE_I16X8_U = 127;
const ARG_ATOMIC_WAKE = 0;
const ARG_I32_ATOMIC_WAIT = 1;
const ARG_I64_ATOMIC_WAIT = 2;
const ARG_I32_ATOMIC_LOAD = 16;
const ARG_I64_ATOMIC_LOAD = 17;
const ARG_I32_ATOMIC_LOAD_8U = 18;
const ARG_I32_ATOMIC_LOAD_16U = 19;
const ARG_I64_ATOMIC_LOAD_8U = 20;
const ARG_I64_ATOMIC_LOAD_16U = 21;
const ARG_I64_ATOMIC_LOAD_32U = 22;
const ARG_I32_ATOMIC_STORE = 23;
const ARG_I64_ATOMIC_STORE = 24;
const ARG_I32_ATOMIC_STORE_8 = 25;
const ARG_I32_ATOMIC_STORE_16 = 26;
const ARG_I64_ATOMIC_STORE_8 = 27;
const ARG_I64_ATOMIC_STORE_16 = 28;
const ARG_I64_ATOMIC_STORE_32 = 29;
const ARG_I32_ATOMIC_RMW_ADD = 30;
const ARG_I64_ATOMIC_RMW_ADD = 31;
const ARG_I32_ATOMIC_RMW_ADD_8U = 32;
const ARG_I32_ATOMIC_RMW_ADD_16U = 33;
const ARG_I64_ATOMIC_RMW_ADD_8U = 34;
const ARG_I64_ATOMIC_RMW_ADD_16U = 35;
const ARG_I64_ATOMIC_RMW_ADD_32U = 36;
const ARG_I32_ATOMIC_RMW_SUB = 37;
const ARG_I64_ATOMIC_RMW_SUB = 38;
const ARG_I32_ATOMIC_RMW_SUB_8U = 39;
const ARG_I32_ATOMIC_RMW_SUB_16U = 40;
const ARG_I64_ATOMIC_RMW_SUB_8U = 41;
const ARG_I64_ATOMIC_RMW_SUB_16U = 42;
const ARG_I64_ATOMIC_RMW_SUB_32U = 43;
const ARG_I32_ATOMIC_RMW_AND = 44;
const ARG_I64_ATOMIC_RMW_AND = 45;
const ARG_I32_ATOMIC_RMW_AND_8U = 46;
const ARG_I32_ATOMIC_RMW_AND_16U = 47;
const ARG_I64_ATOMIC_RMW_AND_8U = 48;
const ARG_I64_ATOMIC_RMW_AND_16U = 49;
const ARG_I64_ATOMIC_RMW_AND_32U = 50;
const ARG_I32_ATOMIC_RMW_OR = 51;
const ARG_I64_ATOMIC_RMW_OR = 52;
const ARG_I32_ATOMIC_RMW_OR_8U = 53;
const ARG_I32_ATOMIC_RMW_OR_16U = 54;
const ARG_I64_ATOMIC_RMW_OR_8U = 55;
const ARG_I64_ATOMIC_RMW_OR_16U = 56;
const ARG_I64_ATOMIC_RMW_OR_32U = 57;
const ARG_I32_ATOMIC_RMW_XOR = 58;
const ARG_I64_ATOMIC_RMW_XOR = 59;
const ARG_I32_ATOMIC_RMW_XOR_8U = 60;
const ARG_I32_ATOMIC_RMW_XOR_16U = 61;
const ARG_I64_ATOMIC_RMW_XOR_8U = 62;
const ARG_I64_ATOMIC_RMW_XOR_16U = 63;
const ARG_I64_ATOMIC_RMW_XOR_32U = 64;
const ARG_I32_ATOMIC_RMW_XCHG = 65;
const ARG_I64_ATOMIC_RMW_XCHG = 66;
const ARG_I32_ATOMIC_RMW_XCHG_8U = 67;
const ARG_I32_ATOMIC_RMW_XCHG_16U = 68;
const ARG_I64_ATOMIC_RMW_XCHG_8U = 69;
const ARG_I64_ATOMIC_RMW_XCHG_16U = 70;
const ARG_I64_ATOMIC_RMW_XCHG_32U = 71;
const ARG_I32_ATOMIC_RMW_CMPXCHG = 72;
const ARG_I64_ATOMIC_RMW_CMPXCHG = 73;
const ARG_I32_ATOMIC_RMW_CMPXCHG_8U = 74;
const ARG_I32_ATOMIC_RMW_CMPXCHG_16U = 75;
const ARG_I64_ATOMIC_RMW_CMPXCHG_8U = 76;
const ARG_I64_ATOMIC_RMW_CMPXCHG_16U = 77;
const ARG_I64_ATOMIC_RMW_CMPXCHG_32U = 78;

const convertOpcode = function(string) {
  const opcodeVal = opcodeStr[string];
  if (typeof opcodeVal === "undefined") {
    throw new Error("Invalid opcode " + string);
  }
  return opcodeVal;
};

const convertOpcodeArray = function(opcodeArray) {
  const result = [];
  for (let i = 0; i < opcodeArray.length; i++) {
    const thisElement = opcodeArray[i];
    let convertedElement = thisElement;
    if (typeof thisElement === "string") {
      convertedElement = convertOpcode(thisElement);
    }
    result.push(convertedElement);
  }
  return result;
};

const Uint8ToArray = function(x) {
  return [x & 255];
};

const Uint32ToArray = function(x) {
  return [x & 255, (x & 65280) >> 8, (x & 16711680) >> 16, (x & 4278190080) >> 24];
};

const Uint64ToArray = function(x) {
  return [
    x & 255,
    (x & 65280) >> 8,
    (x & 16711680) >> 16,
    (x & 4278190080) >> 24,
    (x & 0xff00000000) >> 32,
    (x & 0xff0000000000) >> 40,
    (x & 0xff000000000000) >> 48,
    (x & 0xff00000000000000) >> 56
  ];
};

const VarUint32ToArray = function(x) {
  const result = [];
  let current = x;
  if (x == 0) {
    return [0];
  }
  while (current > 0) {
    let thisByte = current & 127;
    current >>= 7;
    if (current) {
      thisByte |= 128;
    }
    result.push(thisByte);
  }
  return result;
};

const VarSint32ToArray = function(x) {
  const result = [];
  let current = x;
  while (1) {
    thisByte = current & 127;
    current >>= 7;
    if (current == -1 && thisByte & 64) {
      result.push(thisByte);
      break;
    } else if (current == 0 && !(thisByte & 64)) {
      result.push(thisByte);
      break;
    } else {
      thisByte |= 128;
      result.push(thisByte);
    }
  }
  return result;
};

const stringToByteArray = function(str) {
  return str.split("").map(function(c) {
    return c.charCodeAt(0);
  });
};

const VarUint32 = function(value) {
  if (typeof value == "number") {
    return VarUint32ToArray(value);
  } else if (value instanceof WailVariable) {
    return value.varUint32();
  } else {
    // ...
  }
};

class WailVariable {
  constructor() {
    this._value = null;
  }
  get value() {
    if (this._value === null) {
      throw new Error("Attempted to resolve WailVariable before set");
    }
    return this._value;
  }
  set value(newValue) {
    this._value = newValue;
  }
  i32() {
    if (this._value !== null) {
      return this.value;
    }
    return new WailI32(this);
  }
  f32() {
    if (this._value !== null) {
      const f32Array = new Float32Array([this._value]);
      return new Uint8Array(f32Array.buffer);
    }
    return new WailF32(this);
  }
  i64() {
    if (this._value !== null) {
      return this.value;
    }
    return new WailI64(this);
  }
  f64() {
    if (this._value !== null) {
      const f64Array = new Float64Array([this._value]);
      return new Uint8Array(f64Array.buffer);
    }
    return new WailF64(this);
  }
  varUint32() {
    if (this._value !== null) {
      return VarUint32(this.value);
    }
    return new WailVarUint32(this);
  }
}

class TypedWailVariable {
  constructor(parentVariable) {
    this._parent = parentVariable;
  }
}

class WailI32 extends TypedWailVariable {
  get value() {
    return Uint32ToArray(this._parent.value);
  }
}

class WailF32 extends TypedWailVariable {
  get value() {
    return Uint32ToArray(this._parent.value);
  }
}

class WailI64 extends TypedWailVariable {
  get value() {
    return Uint64ToArray(this._parent.value);
  }
}

class WailF64 extends TypedWailVariable {
  get value() {
    return Uint64ToArray(this._parent.value);
  }
}

class WailVarUint32 extends TypedWailVariable {
  get value() {
    return VarUint32ToArray(this._parent.value);
  }
}

const BufferReader = class {
  constructor(buffer) {
    this.inBuffer = null;
    this.outBuffer = null;
    if (typeof buffer !== "undefined") {
      this.inBuffer = new Uint8Array(buffer);
      this.outBuffer = new Uint8Array(buffer.length * 2);
    } else {
      this.outBuffer = new Uint8Array(1);
    }
    this.inPos = 0;
    this._copyPos = 0;
    this.outPos = 0;
    this._anchor = null;
  }
  load(buffer) {
    this.inBuffer = new Uint8Array(buffer);
    this.outBuffer = new Uint8Array(this.inBuffer.length * 2);
  }
  resize() {
    const newBuffer = new Uint8Array(Math.ceil(8 + this.outBuffer.length * 1.25));
    for (let i = 0; i < this.outPos; i++) {
      newBuffer[i] = this.outBuffer[i];
    }
    this.outBuffer = newBuffer;
  }
  readUint8() {
    return this.inBuffer[this.inPos++];
  }
  readUint32() {
    const b1 = this.inBuffer[this.inPos++];
    const b2 = this.inBuffer[this.inPos++];
    const b3 = this.inBuffer[this.inPos++];
    const b4 = this.inBuffer[this.inPos++];
    return b1 | (b2 << 8) | (b3 << 16) | (b4 << 24);
  }
  readVarUint32() {
    let result = 0;
    let shift = 0;
    let currentByte;
    do {
      currentByte = this.readUint8();
      result |= (currentByte & 127) << shift;
      shift += 7;
    } while (currentByte & 128);
    return result;
  }
  readUint64() {
    const b1 = this.inBuffer[this.inPos++];
    const b2 = this.inBuffer[this.inPos++];
    const b3 = this.inBuffer[this.inPos++];
    const b4 = this.inBuffer[this.inPos++];
    const b5 = this.inBuffer[this.inPos++];
    const b6 = this.inBuffer[this.inPos++];
    const b7 = this.inBuffer[this.inPos++];
    const b8 = this.inBuffer[this.inPos++];
    return (
      b1 |
      (b2 << 8) |
      (b3 << 16) |
      (b4 << 24) |
      (b5 << 32) |
      (b6 << 40) |
      (b7 << 48) |
      (b8 << 56)
    );
  }
  readUint128() {
    const b1 = this.inBuffer[this.inPos++];
    const b2 = this.inBuffer[this.inPos++];
    const b3 = this.inBuffer[this.inPos++];
    const b4 = this.inBuffer[this.inPos++];
    const b5 = this.inBuffer[this.inPos++];
    const b6 = this.inBuffer[this.inPos++];
    const b7 = this.inBuffer[this.inPos++];
    const b8 = this.inBuffer[this.inPos++];
    const b9 = this.inBuffer[this.inPos++];
    const b10 = this.inBuffer[this.inPos++];
    const b11 = this.inBuffer[this.inPos++];
    const b12 = this.inBuffer[this.inPos++];
    const b13 = this.inBuffer[this.inPos++];
    const b14 = this.inBuffer[this.inPos++];
    const b15 = this.inBuffer[this.inPos++];
    const b16 = this.inBuffer[this.inPos++];
    return (
      b1 |
      (b2 << 8) |
      (b3 << 16) |
      (b4 << 24) |
      (b5 << 32) |
      (b6 << 40) |
      (b7 << 48) |
      (b8 << 56) |
      (b9 << 64) |
      (b10 << 72) |
      (b11 << 80) |
      (b12 << 88) |
      (b13 << 96) |
      (b14 << 104) |
      (b15 << 112) |
      (b16 << 120)
    );
  }
  // ...
};
    
