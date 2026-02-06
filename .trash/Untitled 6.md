[
    // ====================
    // MATH MODE & BASICS
    // ====================
	{trigger: "mk", replacement: "$$0$", options: "tA"},
	{trigger: "dm", replacement: "$$\n$0\n$$", options: "tAw"},
	{trigger: "beg", replacement: "\\begin{$0}\n$1\n\\end{$0}", options: "mA"},

    // ====================
    // SUBSCRIPTS & SUPERSCRIPTS (Enhanced with up/down)
    // ====================
	{trigger: "sr", replacement: "^{2}", options: "mA"},
	{trigger: "cb", replacement: "^{3}", options: "mA"},
	{trigger: "rd", replacement: "^{$0}$1", options: "mA"},
	{trigger: "uu", replacement: "^{$0}$1", options: "mA"},  // "up" for superscript
	{trigger: "dd", replacement: "_{$0}$1", options: "mA"},  // "down" for subscript
	{trigger: "ud", replacement: "^{$0}_{$1}$2", options: "mA"},  // both up and down
	{trigger: "_", replacement: "_{$0}$1", options: "mA"},
	{trigger: "sts", replacement: "_\\text{$0}", options: "mA"},
    {trigger: "invs", replacement: "^{-1}", options: "mA"},
    {trigger: /([A-Za-z])(\d)/, replacement: "[[0]]_{[[1]]}", options: "rmA", description: "Auto letter subscript", priority: -1},
    {trigger: /([A-Za-z])_(\d\d)/, replacement: "[[0]]_{[[1]]}", options: "rmA"},
	{trigger: /\\hat{([A-Za-z])}(\d)/, replacement: "\\hat{[[0]]}_{[[1]]}", options: "rmA"},
	{trigger: /\\vec{([A-Za-z])}(\d)/, replacement: "\\vec{[[0]]}_{[[1]]}", options: "rmA"},
	{trigger: /\\mathbf{([A-Za-z])}(\d)/, replacement: "\\mathbf{[[0]]}_{[[1]]}", options: "rmA"},
    {trigger: "xnn", replacement: "x_{n}", options: "mA"},
	{trigger: "xii", replacement: "x_{i}", options: "mA", priority: 1},
	{trigger: "xjj", replacement: "x_{j}", options: "mA"},
	{trigger: "xp1", replacement: "x_{n+1}", options: "mA"},
	
    // Tensor indices
    {trigger: /T(\d)(\d)/, replacement: "T^{[[0]]}_{[[1]]}", options: "rmA"},

    // ====================
    // GREEK LETTERS
    // ====================
	{trigger: "@a", replacement: "\\alpha", options: "mA"},
	{trigger: "@b", replacement: "\\beta", options: "mA"},
	{trigger: "@g", replacement: "\\gamma", options: "mA"},
	{trigger: "@G", replacement: "\\Gamma", options: "mA"},
	{trigger: "@d", replacement: "\\delta", options: "mA"},
	{trigger: "@D", replacement: "\\Delta", options: "mA"},
	{trigger: "@e", replacement: "\\epsilon", options: "mA"},
	{trigger: ":e", replacement: "\\varepsilon", options: "mA"},
	{trigger: "@z", replacement: "\\zeta", options: "mA"},
	{trigger: "@t", replacement: "\\theta", options: "mA"},
	{trigger: "@T", replacement: "\\Theta", options: "mA"},
	{trigger: ":t", replacement: "\\vartheta", options: "mA"},
	{trigger: "@i", replacement: "\\iota", options: "mA"},
	{trigger: "@k", replacement: "\\kappa", options: "mA"},
	{trigger: "@l", replacement: "\\lambda", options: "mA"},
	{trigger: "@L", replacement: "\\Lambda", options: "mA"},
	{trigger: "@s", replacement: "\\sigma", options: "mA"},
	{trigger: "@S", replacement: "\\Sigma", options: "mA"},
	{trigger: "@u", replacement: "\\upsilon", options: "mA"},
	{trigger: "@U", replacement: "\\Upsilon", options: "mA"},
	{trigger: "@o", replacement: "\\omega", options: "mA"},
	{trigger: "@O", replacement: "\\Omega", options: "mA"},
	{trigger: "@m", replacement: "\\mu", options: "mA"},
	{trigger: "@n", replacement: "\\nu", options: "mA"},
	{trigger: "@x", replacement: "\\xi", options: "mA"},
	{trigger: "@X", replacement: "\\Xi", options: "mA"},
	{trigger: "@p", replacement: "\\pi", options: "mA"},
	{trigger: "@P", replacement: "\\Pi", options: "mA"},
	{trigger: ":p", replacement: "\\varpi", options: "mA"},
	{trigger: "@r", replacement: "\\rho", options: "mA"},
	{trigger: ":r", replacement: "\\varrho", options: "mA"},
	{trigger: "@f", replacement: "\\phi", options: "mA"},
	{trigger: "@F", replacement: "\\Phi", options: "mA"},
	{trigger: ":f", replacement: "\\varphi", options: "mA"},
	{trigger: "@c", replacement: "\\chi", options: "mA"},
	{trigger: "@y", replacement: "\\psi", options: "mA"},
	{trigger: "@Y", replacement: "\\Psi", options: "mA"},
	{trigger: "ome", replacement: "\\omega", options: "mA"},
	{trigger: "Ome", replacement: "\\Omega", options: "mA"},

    // ====================
    // TEXT ENVIRONMENT
    // ====================
    {trigger: "text", replacement: "\\text{$0}$1", options: "mA"},
    {trigger: "\"", replacement: "\\text{$0}$1", options: "mA"},

    // ====================
    // BASIC OPERATIONS
    // ====================
	{trigger: "sq", replacement: "\\sqrt{ $0 }$1", options: "mA"},
	{trigger: "//", replacement: "\\frac{$0}{$1}$2", options: "mA"},
	{trigger: "ee", replacement: "e^{ $0 }$1", options: "mA"},
    {trigger: /([^\\])(exp|log|ln)/, replacement: "[[0]]\\[[1]]", options: "rmA"},
    {trigger: "conj", replacement: "^{*}", options: "mA"},
    {trigger: "Re", replacement: "\\mathrm{Re}", options: "mA"},
	{trigger: "Im", replacement: "\\mathrm{Im}", options: "mA"},
    {trigger: "bf", replacement: "\\mathbf{$0}$1", options: "mA"},
	{trigger: "rm", replacement: "\\mathrm{$0}$1", options: "mA"},
    {trigger: "cal", replacement: "\\mathcal{$0}$1", options: "mA"},
	{trigger: "bb", replacement: "\\mathbb{$0}$1", options: "mA"},
	{trigger: "frak", replacement: "\\mathfrak{$0}$1", options: "mA"},
	{trigger: "scr", replacement: "\\mathscr{$0}$1", options: "mA"},

    // ====================
    // LINEAR ALGEBRA
    // ====================
    {trigger: /([^\\])(det)/, replacement: "[[0]]\\[[1]]", options: "rmA"},
    {trigger: "trace", replacement: "\\mathrm{Tr}", options: "mA"},
	{trigger: "Tr", replacement: "\\mathrm{Tr}", options: "mA"},
	{trigger: "rank", replacement: "\\mathrm{rank}", options: "mA"},
	{trigger: "dim", replacement: "\\dim", options: "mA"},
	{trigger: "span", replacement: "\\mathrm{span}", options: "mA"},
	{trigger: "ker", replacement: "\\ker", options: "mA"},
	{trigger: "img", replacement: "\\mathrm{im}", options: "mA"},
	{trigger: "coker", replacement: "\\mathrm{coker}", options: "mA"},
	{trigger: "diag", replacement: "\\mathrm{diag}", options: "mA"},
	{trigger: "tr", replacement: "^{T}", options: "mA"},
	{trigger: "trans", replacement: "^{\\top}", options: "mA"},

    // ====================
    // ACCENTS & DECORATIONS
    // ====================
	{trigger: "([a-zA-Z])hat", replacement: "\\hat{[[0]]}", options: "rmA"},
    {trigger: "([a-zA-Z])bar", replacement: "\\bar{[[0]]}", options: "rmA"},
	{trigger: "([a-zA-Z])dot", replacement: "\\dot{[[0]]}", options: "rmA", priority: -1},
	{trigger: "([a-zA-Z])ddot", replacement: "\\ddot{[[0]]}", options: "rmA", priority: 1},
	{trigger: "([a-zA-Z])tilde", replacement: "\\tilde{[[0]]}", options: "rmA"},
	{trigger: "([a-zA-Z])und", replacement: "\\underline{[[0]]}", options: "rmA"},
	{trigger: "([a-zA-Z])vec", replacement: "\\vec{[[0]]}", options: "rmA"},
    {trigger: "([a-zA-Z]),\\.", replacement: "\\mathbf{[[0]]}", options: "rmA"},
	{trigger: "([a-zA-Z])\\.,", replacement: "\\mathbf{[[0]]}", options: "rmA"},
	{trigger: "\\\\(${GREEK}),\\.", replacement: "\\boldsymbol{\\[[0]]}", options: "rmA"},
	{trigger: "\\\\(${GREEK})\\.,", replacement: "\\boldsymbol{\\[[0]]}", options: "rmA"},

	{trigger: "hat", replacement: "\\hat{$0}$1", options: "mA"},
    {trigger: "bar", replacement: "\\bar{$0}$1", options: "mA"},
	{trigger: "dot", replacement: "\\dot{$0}$1", options: "mA", priority: -1},
	{trigger: "ddot", replacement: "\\ddot{$0}$1", options: "mA"},
	{trigger: "cdot", replacement: "\\cdot", options: "mA"},
	{trigger: "tilde", replacement: "\\tilde{$0}$1", options: "mA"},
	{trigger: "und", replacement: "\\underline{$0}$1", options: "mA"},
	{trigger: "vec", replacement: "\\vec{$0}$1", options: "mA"},
	{trigger: "overline", replacement: "\\overline{$0}$1", options: "mA"},
	{trigger: "widetilde", replacement: "\\widetilde{$0}$1", options: "mA"},
	{trigger: "widehat", replacement: "\\widehat{$0}$1", options: "mA"},

    // ====================
    // SYMBOLS & OPERATORS
    // ====================
    {trigger: "ooo", replacement: "\\infty", options: "mA"},
	{trigger: "oo", replacement: "\\infty", options: "mA"},
	{trigger: "8oo", replacement: "\\infty", options: "mA"},
	{trigger: "sum", replacement: "\\sum", options: "mA"},
	{trigger: "prod", replacement: "\\prod", options: "mA"},
	{trigger: "\\sum", replacement: "\\sum_{${0:i}=${1:1}}^{${2:N}} $3", options: "m"},
	{trigger: "\\prod", replacement: "\\prod_{${0:i}=${1:1}}^{${2:N}} $3", options: "m"},
    {trigger: "lim", replacement: "\\lim_{ ${0:n} \\to ${1:\\infty} } $2", options: "mA"},
	{trigger: "limsup", replacement: "\\limsup_{${0:n} \\to ${1:\\infty}} $2", options: "mA"},
	{trigger: "liminf", replacement: "\\liminf_{${0:n} \\to ${1:\\infty}} $2", options: "mA"},
	{trigger: "sup", replacement: "\\sup", options: "mA"},
	{trigger: "inf", replacement: "\\inf", options: "mA"},
	{trigger: "max", replacement: "\\max", options: "mA"},
	{trigger: "min", replacement: "\\min", options: "mA"},
	{trigger: "argmax", replacement: "\\operatorname*{argmax}", options: "mA"},
	{trigger: "argmin", replacement: "\\operatorname*{argmin}", options: "mA"},
    {trigger: "+-", replacement: "\\pm", options: "mA"},
	{trigger: "-+", replacement: "\\mp", options: "mA"},
	{trigger: "+/-", replacement: "\\pm", options: "mA"},
	{trigger: "-/+", replacement: "\\mp", options: "mA"},
    {trigger: "...", replacement: "\\dots", options: "mA"},
	{trigger: "ldots", replacement: "\\ldots", options: "mA"},
	{trigger: "cdots", replacement: "\\cdots", options: "mA"},
	{trigger: "vdots", replacement: "\\vdots", options: "mA"},
	{trigger: "ddots", replacement: "\\ddots", options: "mA"},
    {trigger: "nabl", replacement: "\\nabla", options: "mA"},
	{trigger: "del", replacement: "\\nabla", options: "mA"},
	{trigger: "grad", replacement: "\\nabla", options: "mA"},
	{trigger: "div", replacement: "\\nabla \\cdot", options: "mA"},
	{trigger: "curl", replacement: "\\nabla \\times", options: "mA"},
    {trigger: "xx", replacement: "\\times", options: "mA"},
	{trigger: "ox", replacement: "\\otimes", options: "mA"},
	{trigger: "o+", replacement: "\\oplus", options: "mA"},
	{trigger: "o.", replacement: "\\odot", options: "mA"},
	{trigger: "o-", replacement: "\\ominus", options: "mA"},
	{trigger: "o/", replacement: "\\oslash", options: "mA"},
    {trigger: "**", replacement: "\\cdot", options: "mA"},
	{trigger: "*", replacement: "\\ast", options: "mA"},
	{trigger: "***", replacement: "\\star", options: "mA"},
    {trigger: "para", replacement: "\\parallel", options: "mA"},
	{trigger: "perp", replacement: "\\perp", options: "mA"},
	{trigger: "_|_", replacement: "\\perp", options: "mA"},
	{trigger: "|=", replacement: "\\models", options: "mA"},
	{trigger: "|==", replacement: "\\vDash", options: "mA"},
	{trigger: "||=", replacement: "\\Vdash", options: "mA"},
	{trigger: "||==", replacement: "\\VDash", options: "mA"},
	{trigger: "|/-", replacement: "\\nvdash", options: "mA"},
	{trigger: "||/-", replacement: "\\nVdash", options: "mA"},
	{trigger: "angle", replacement: "\\angle", options: "mA"},
	{trigger: "/_", replacement: "\\angle", options: "mA"},
	{trigger: "measuredangle", replacement: "\\measuredangle", options: "mA"},
	{trigger: "sphericalangle", replacement: "\\sphericalangle", options: "mA"},
	{trigger: "triangle", replacement: "\\triangle", options: "mA"},
	{trigger: "square", replacement: "\\square", options: "mA"},
	{trigger: "diamond", replacement: "\\diamond", options: "mA"},
	{trigger: "Box", replacement: "\\Box", options: "mA"},
	{trigger: "Diamond", replacement: "\\Diamond", options: "mA"},
	{trigger: "aleph", replacement: "\\aleph", options: "mA"},
	{trigger: "beth", replacement: "\\beth", options: "mA"},
	{trigger: "daleth", replacement: "\\daleth", options: "mA"},
	{trigger: "gimel", replacement: "\\gimel", options: "mA"},
	{trigger: "partial", replacement: "\\partial", options: "mA"},
	{trigger: "prime", replacement: "\\prime", options: "mA"},
	{trigger: "''", replacement: "^{\\prime\\prime}", options: "mA"},
	{trigger: "'''", replacement: "^{\\prime\\prime\\prime}", options: "mA"},
	{trigger: "deg", replacement: "^{\\circ}", options: "mA"},
	{trigger: "%%", replacement: "\\%", options: "mA"},
	{trigger: "##", replacement: "\\#", options: "mA"},
	{trigger: "&&", replacement: "\\&", options: "mA"},

    // ====================
    // RELATIONS
    // ====================
	{trigger: "===", replacement: "\\equiv", options: "mA"},
	{trigger: "==", replacement: "\\equiv", options: "mA"},
    {trigger: "!=", replacement: "\\neq", options: "mA"},
	{trigger: "/=", replacement: "\\neq", options: "mA"},
	{trigger: "=/=", replacement: "\\neq", options: "mA"},
	{trigger: ">=", replacement: "\\geq", options: "mA"},
	{trigger: "<=", replacement: "\\leq", options: "mA"},
	{trigger: ">>", replacement: "\\gg", options: "mA"},
	{trigger: "<<", replacement: "\\ll", options: "mA"},
	{trigger: "<<<", replacement: "\\lll", options: "mA"},
	{trigger: ">>>", replacement: "\\ggg", options: "mA"},
	{trigger: "!>", replacement: "\\ngtr", options: "mA"},
	{trigger: "!<", replacement: "\\nless", options: "mA"},
	{trigger: "!>=", replacement: "\\ngeq", options: "mA"},
	{trigger: "!<=", replacement: "\\nleq", options: "mA"},
	{trigger: "~~", replacement: "\\sim", options: "mA"},
	{trigger: "~=", replacement: "\\simeq", options: "mA"},
	{trigger: "~-", replacement: "\\simeq", options: "mA"},
	{trigger: "~~", replacement: "\\approx", options: "mA"},
	{trigger: "simm", replacement: "\\sim", options: "mA"},
	{trigger: "sim=", replacement: "\\simeq", options: "mA"},
    {trigger: "prop", replacement: "\\propto", options: "mA"},
	{trigger: "propto", replacement: "\\propto", options: "mA"},
	{trigger: "oc", replacement: "\\propto", options: "mA"},
	{trigger: "approx", replacement: "\\approx", options: "mA"},
	{trigger: ":=", replacement: "\\coloneqq", options: "mA"},
	{trigger: "=:", replacement: "\\eqqcolon", options: "mA"},
	{trigger: "::=", replacement: "\\Coloneqq", options: "mA"},
	{trigger: "=::", replacement: "\\Eqqcolon", options: "mA"},
	{trigger: "::", replacement: "\\colon", options: "mA"},
	{trigger: "cong", replacement: "\\cong", options: "mA"},
	{trigger: "~==", replacement: "\\cong", options: "mA"},
	{trigger: "iso", replacement: "\\cong", options: "mA"},
	{trigger: "eqv", replacement: "\\simeq", options: "mA"},
	{trigger: "homeo", replacement: "\\cong", options: "mA"},
	{trigger: "homot", replacement: "\\simeq", options: "mA"},
	{trigger: "doteq", replacement: "\\doteq", options: "mA"},
	{trigger: ".=", replacement: "\\doteq", options: "mA"},
	{trigger: "==.", replacement: "\\doteqdot", options: "mA"},
	{trigger: "||", replacement: "\\parallel", options: "mA"},
	{trigger: "asymp", replacement: "\\asymp", options: "mA"},
	{trigger: "bowtie", replacement: "\\bowtie", options: "mA"},
	{trigger: "><", replacement: "\\bowtie", options: "mA"},
	{trigger: "smile", replacement: "\\smile", options: "mA"},
	{trigger: "frown", replacement: "\\frown", options: "mA"},
	{trigger: "prec", replacement: "\\prec", options: "mA"},
	{trigger: "succ", replacement: "\\succ", options: "mA"},
	{trigger: "preceq", replacement: "\\preceq", options: "mA"},
	{trigger: "succeq", replacement: "\\succeq", options: "mA"},
	{trigger: "-<", replacement: "\\prec", options: "mA"},
	{trigger: ">-", replacement: "\\succ", options: "mA"},
	{trigger: "-<=", replacement: "\\preceq", options: "mA"},
	{trigger: ">=-", replacement: "\\succeq", options: "mA"},
	{trigger: "mid", replacement: "\\mid", options: "mA"},
	{trigger: "nmid", replacement: "\\nmid", options: "mA"},
	{trigger: "divides", replacement: "\\mid", options: "mA"},
	{trigger: "ndivides", replacement: "\\nmid", options: "mA"},

    // ====================
    // ARROWS
    // ====================
    {trigger: "<->", replacement: "\\leftrightarrow", options: "mA"},
	{trigger: "<=>", replacement: "\\Leftrightarrow", options: "mA"},
	{trigger: "->", replacement: "\\to", options: "mA"},
	{trigger: "<-", replacement: "\\gets", options: "mA"},
	{trigger: "-->", replacement: "\\longrightarrow", options: "mA"},
	{trigger: "<--", replacement: "\\longleftarrow", options: "mA"},
	{trigger: "<-->", replacement: "\\longleftrightarrow", options: "mA"},
	{trigger: "!>", replacement: "\\mapsto", options: "mA"},
	{trigger: "<!", replacement: "\\mapsfrom", options: "mA"},
	{trigger: "|->", replacement: "\\mapsto", options: "mA"},
	{trigger: "<-|", replacement: "\\mapsfrom", options: "mA"},
    {trigger: "=>", replacement: "\\implies", options: "mA"},
	{trigger: "=<", replacement: "\\impliedby", options: "mA"},
	{trigger: "iff", replacement: "\\iff", options: "mA"},
	{trigger: "==>", replacement: "\\Longrightarrow", options: "mA"},
	{trigger: "<==", replacement: "\\Longleftarrow", options: "mA"},
	{trigger: "<==>", replacement: "\\Longleftrightarrow", options: "mA"},
	{trigger: "~>", replacement: "\\rightsquigarrow", options: "mA"},
	{trigger: ">->", replacement: "\\hookrightarrow", options: "mA"},
	{trigger: "<-<", replacement: "\\hookleftarrow", options: "mA"},
	{trigger: "->>", replacement: "\\twoheadrightarrow", options: "mA"},
	{trigger: "<<-", replacement: "\\twoheadleftarrow", options: "mA"},
	{trigger: "upto", replacement: "\\uparrow", options: "mA"},
	{trigger: "downto", replacement: "\\downarrow", options: "mA"},
	{trigger: "^^", replacement: "\\uparrow", options: "mA"},
	{trigger: "vv", replacement: "\\downarrow", options: "mA"},
	{trigger: "||^", replacement: "\\Uparrow", options: "mA"},
	{trigger: "||v", replacement: "\\Downarrow", options: "mA"},
	{trigger: "xto", replacement: "\\xrightarrow{$0}$1", options: "mA"},
	{trigger: "xfrom", replacement: "\\xleftarrow{$0}$1", options: "mA"},
	{trigger: "xtofrom", replacement: "\\xleftrightarrow{$0}$1", options: "mA"},

    // ====================
    // SET THEORY
    // ====================
	{trigger: "eset", replacement: "\\emptyset", options: "mA"},
	{trigger: "empty", replacement: "\\emptyset", options: "mA"},
	{trigger: "0/", replacement: "\\emptyset", options: "mA"},
	{trigger: "set", replacement: "\\{ $0 \\}$1", options: "mA"},
	{trigger: "inn", replacement: "\\in", options: "mA"},
	{trigger: "!in", replacement: "\\notin", options: "mA"},
	{trigger: "notin", replacement: "\\notin", options: "mA"},
	{trigger: "nin", replacement: "\\notin", options: "mA"},
	{trigger: "and", replacement: "\\cap", options: "mA"},
	{trigger: "orr", replacement: "\\cup", options: "mA"},
	{trigger: "union", replacement: "\\cup", options: "mA"},
	{trigger: "inter", replacement: "\\cap", options: "mA"},
	{trigger: "nn", replacement: "\\cap", options: "mA"},
	{trigger: "Union", replacement: "\\bigcup", options: "mA"},
	{trigger: "Inter", replacement: "\\bigcap", options: "mA"},
	{trigger: "UU", replacement: "\\bigcup", options: "mA"},
	{trigger: "NN", replacement: "\\bigcap", options: "mA"},
    {trigger: "\\\\\\", replacement: "\\setminus", options: "mA"},
	{trigger: "\\\\", replacement: "\\setminus", options: "mA"},
    {trigger: "sub", replacement: "\\subset", options: "mA"},
	{trigger: "sup", replacement: "\\supset", options: "mA"},
	{trigger: "sube", replacement: "\\subseteq", options: "mA"},
	{trigger: "supe", replacement: "\\supseteq", options: "mA"},
	{trigger: "sub=", replacement: "\\subseteq", options: "mA"},
	{trigger: "sup=", replacement: "\\supseteq", options: "mA"},
	{trigger: "c=", replacement: "\\subseteq", options: "mA"},
	{trigger: "c==", replacement: "\\supseteq", options: "mA"},
	{trigger: "!sub", replacement: "\\not\\subset", options: "mA"},
	{trigger: "!sube", replacement: "\\nsubseteq", options: "mA"},
	{trigger: "!supe", replacement: "\\nsupseteq", options: "mA"},
	{trigger: "dunion", replacement: "\\sqcup", options: "mA"},
	{trigger: "dUnion", replacement: "\\bigsqcup", options: "mA"},
	{trigger: "sq+", replacement: "\\sqcup", options: "mA"},
	{trigger: "Sq+", replacement: "\\bigsqcup", options: "mA"},
	{trigger: "e\\xi sts", replacement: "\\exists", options: "mA", priority: 1},
	{trigger: "EE", replacement: "\\exists", options: "mA"},
	{trigger: "AA", replacement: "\\forall", options: "mA"},
	{trigger: "forall", replacement: "\\forall", options: "mA"},
	{trigger: "!EE", replacement: "\\nexists", options: "mA"},
	{trigger: "nexists", replacement: "\\nexists", options: "mA"},

    // ====================
    // COMMON SETS
    // ====================
	{trigger: "NN", replacement: "\\mathbb{N}", options: "mA"},
	{trigger: "ZZ", replacement: "\\mathbb{Z}", options: "mA"},
	{trigger: "QQ", replacement: "\\mathbb{Q}", options: "mA"},
	{trigger: "RR", replacement: "\\mathbb{R}", options: "mA"},
	{trigger: "CC", replacement: "\\mathbb{C}", options: "mA"},
	{trigger: "HH", replacement: "\\mathbb{H}", options: "mA"},
	{trigger: "PP", replacement: "\\mathbb{P}", options: "mA"},
	{trigger: "FF", replacement: "\\mathbb{F}", options: "mA"},
	{trigger: "LL", replacement: "\\mathcal{L}", options: "mA"},

    // ====================
    // CALCULUS & ANALYSIS
    // ====================
    {trigger: "par", replacement: "\\frac{ \\partial ${0:y} }{ \\partial ${1:x} } $2", options: "m"},
    {trigger: /pa([A-Za-z])([A-Za-z])/, replacement: "\\frac{ \\partial [[0]] }{ \\partial [[1]] } ", options: "rm"},
	{trigger: "pa2", replacement: "\\frac{ \\partial^{2} ${0:y} }{ \\partial ${1:x}^{2} } $2", options: "mA"},
	{trigger: "pa3", replacement: "\\frac{ \\partial^{3} ${0:y} }{ \\partial ${1:x}^{3} } $2", options: "mA"},
    {trigger: "ddt", replacement: "\\frac{d}{dt} ", options: "mA"},
	{trigger: "ddx", replacement: "\\frac{d}{dx} ", options: "mA"},
	{trigger: "ddy", replacement: "\\frac{dy}{dx}", options: "mA"},
	{trigger: /dd([A-Za-z])/, replacement: "\\frac{d}{d[[0]]} ", options: "rmA"},

    // Integrals
    {trigger: /([^\\])int/, replacement: "[[0]]\\int", options: "rmA", priority: -1},
    {trigger: "\\int", replacement: "\\int $0 \\, d${1:x} $2", options: "m"},
    {trigger: "dint", replacement: "\\int_{${0:0}}^{${1:1}} $2 \\, d${3:x} $4", options: "mA"},
    {trigger: "oint", replacement: "\\oint", options: "mA"},
	{trigger: "iint", replacement: "\\iint", options: "mA"},
    {trigger: "iiint", replacement: "\\iiint", options: "mA"},
    {trigger: "oinf", replacement: "\\int_{0}^{\\infty} $0 \\, d${1:x} $2", options: "mA"},
	{trigger: "infi", replacement: "\\int_{-\\infty}^{\\infty} $0 \\, d${1:x} $2", options: "mA"},

    // ====================
    // CATEGORY THEORY
    // ====================
	{trigger: "comp", replacement: "\\circ", options: "mA"},
	{trigger: "nat", replacement: "\\Rightarrow", options: "mA"},
	{trigger: "twoto", replacement: "\\rightrightarrows", options: "mA"},
	{trigger: "adj", replacement: "\\dashv", options: "mA"},
	{trigger: "hom", replacement: "\\mathrm{Hom}", options: "mA"},
	{trigger: "Hom", replacement: "\\mathrm{Hom}", options: "mA"},
	{trigger: "mor", replacement: "\\mathrm{Mor}", options: "mA"},
	{trigger: "obj", replacement: "\\mathrm{Ob}", options: "mA"},
	{trigger: "id", replacement: "\\mathrm{id}", options: "mA"},
	{trigger: "Id", replacement: "\\mathrm{Id}", options: "mA"},
	{trigger: "op", replacement: "^{\\mathrm{op}}", options: "mA"},
	{trigger: "cat", replacement: "\\mathbf{$0}$1", options: "mA"},
	{trigger: "Cat", replacement: "\\mathbf{Cat}", options: "mA"},
	{trigger: "Set", replacement: "\\mathbf{Set}", options: "mA"},
	{trigger: "Grp", replacement: "\\mathbf{Grp}", options: "mA"},
	{trigger: "Top", replacement: "\\mathbf{Top}", options: "mA"},
	{trigger: "Fun", replacement: "\\mathrm{Fun}", options: "mA"},
	{trigger: "Nat", replacement: "\\mathrm{Nat}", options: "mA"},
	{trigger: "colim", replacement: "\\operatorname{colim}", options: "mA"},
	{trigger: "End", replacement: "\\mathrm{End}", options: "mA"},
	{trigger: "Aut", replacement: "\\mathrm{Aut}", options: "mA"},
	{trigger: "aut", replacement: "\\mathrm{Aut}", options: "mA"},

    // ====================
    // TYPE THEORY & LOGIC
    // ====================
	{trigger: "judg", replacement: "\\vdash", options: "mA"},
	{trigger: "|-", replacement: "\\vdash", options: "mA"},
	{trigger: "-|", replacement: "\\dashv", options: "mA"},
	{trigger: "|--", replacement: "\\vdash", options: "mA"},
	{trigger: "||--", replacement: "\\Vdash", options: "mA"},
	{trigger: "ctx", replacement: "\\Gamma", options: "mA"},
	{trigger: "defeq", replacement: "\\equiv", options: "mA"},
	{trigger: "jdeq", replacement: ":\\equiv", options: "mA"},
	{trigger: "lam", replacement: "\\lambda $0. $1", options: "mA"},
	{trigger: "nott", replacement: "\\neg", options: "mA"},
	{trigger: "neg", replacement: "\\neg", options: "mA"},
	{trigger: "!!", replacement: "\\neg", options: "mA"},
	{trigger: "land", replacement: "\\land", options: "mA"},
	{trigger: "lor", replacement: "\\lor", options: "mA"},
	{trigger: "/\\", replacement: "\\wedge", options: "mA"},
	{trigger: "\\/", replacement: "\\vee", options: "mA"},
	{trigger: "top", replacement: "\\top", options: "mA"},
	{trigger: "bot", replacement: "\\bot", options: "mA"},
	{trigger: "TT", replacement: "\\top", options: "mA"},
	{trigger: "FF", replacement: "\\bot", options: "mA"},
	{trigger: "models", replacement: "\\models", options: "mA"},
	{trigger: "entails", replacement: "\\vdash", options: "mA"},
	{trigger: "proves", replacement: "\\vdash", options: "mA"},
	{trigger: "therefore", replacement: "\\therefore", options: "mA"},
	{trigger: "...", replacement: "\\therefore", options: "mA"},
	{trigger: "because", replacement: "\\because", options: "mA"},
	{trigger: "QED", replacement: "\\qed", options: "mA"},
	{trigger: "contradiction", replacement: "\\lightning", options: "mA"},

    // ====================
    // TOPOLOGY
    // ====================
	{trigger: "interior", replacement: "^{\\circ}", options: "mA"},
	{trigger: "closure", replacement: "\\overline{$0}$1", options: "mA"},
	{trigger: "nbhd", replacement: "\\mathcal{N}", options: "mA"},
	{trigger: "homgrp", replacement: "\\pi_{$0}$1", options: "mA"},
	{trigger: "fund", replacement: "\\pi_{1}", options: "mA"},

    // ====================
    // DIFFERENTIAL GEOMETRY
    // ====================
	{trigger: "mfd", replacement: "\\mathcal{M}", options: "mA"},
	{trigger: "chart", replacement: "\\varphi", options: "mA"},
	{trigger: "Lie", replacement: "\\mathcal{L}", options: "mA"},
	{trigger: "pushf", replacement: "_{*}", options: "mA"},
	{trigger: "pullb", replacement: "^{*}", options: "mA"},
	{trigger: "wedge", replacement: "\\wedge", options: "mA"},
	{trigger: "Wedge", replacement: "\\bigwedge", options: "mA"},
	{trigger: "vee", replacement: "\\vee", options: "mA"},
	{trigger: "Vee", replacement: "\\bigvee", options: "mA"},
	
	// Differential forms
	{trigger: "dd", replacement: "\\mathrm{d}", options: "mA"},
	{trigger: /([^\\])d([xyzuvwrst])/, replacement: "[[0]]\\mathrm{d}[[1]]", options: "rmA"},
	{trigger: "form", replacement: "\\omega", options: "mA"},
	{trigger: "dform", replacement: "\\mathrm{d}\\omega", options: "mA"},
	{trigger: "hodge", replacement: "\\star", options: "mA"},

	// Covariant derivatives and connections
	{trigger: "nab", replacement: "\\nabla", options: "mA"},
	{trigger: "nabla", replacement: "\\nabla_{$0}$1", options: "mA"},
	{trigger: "cov", replacement: "\\nabla_{$0}$1", options: "mA"},
	
	// Metric and curvature
	{trigger: "metric", replacement: "g_{$0}$1", options: "mA"},
	{trigger: "Christ", replacement: "\\Gamma^{$0}_{$1}$2", options: "mA"},
	{trigger: "Riem", replacement: "R^{$0}_{$1}$2", options: "mA"},
	{trigger: "Ricci", replacement: "R_{$0}$1", options: "mA"},
	{trigger: "Rscalar", replacement: "\\mathcal{R}", options: "mA"},
	{trigger: "Weyl", replacement: "C^{$0}_{$1}$2", options: "mA"},
	{trigger: "Ein", replacement: "G_{$0}$1", options: "mA"},

    // ====================
    // ALGEBRA
    // ====================
	{trigger: "inn", replacement: "\\mathrm{Inn}", options: "mA"},
	{trigger: "out", replacement: "\\mathrm{Out}", options: "mA"},
	{trigger: "GL", replacement: "\\mathrm{GL}", options: "mA"},
	{trigger: "SL", replacement: "\\mathrm{SL}", options: "mA"},
	{trigger: "SO", replacement: "\\mathrm{SO}", options: "mA"},
	{trigger: "SU", replacement: "\\mathrm{SU}", options: "mA"},
	{trigger: "U", replacement: "\\mathrm{U}", options: "mA"},
	{trigger: "O", replacement: "\\mathrm{O}", options: "mA"},
	{trigger: "Sp", replacement: "\\mathrm{Sp}", options: "mA"},
	{trigger: "normal", replacement: "\\triangleleft", options: "mA"},
	{trigger: "normaleq", replacement: "\\trianglelefteq", options: "mA"},
	{trigger: "quot", replacement: "/ \\!", options: "mA"},
	{trigger: "dsum", replacement: "\\oplus", options: "mA"},
	{trigger: "dprod", replacement: "\\otimes", options: "mA"},
	{trigger: "Dsum", replacement: "\\bigoplus", options: "mA"},
	{trigger: "Dprod", replacement: "\\bigotimes", options: "mA"},
	{trigger: "tensor", replacement: "\\otimes", options: "mA"},
	{trigger: "Tensor", replacement: "\\bigotimes", options: "mA"},

    // ====================
    // QUANTUM MECHANICS
    // ====================
	{trigger: "bra", replacement: "\\langle $0 |", options: "mA"},
	{trigger: "ket", replacement: "| $0 \\rangle", options: "mA"},
	{trigger: "brk", replacement: "\\langle $0 | $1 \\rangle $2", options: "mA"},
	{trigger: "braket", replacement: "\\langle $0 | $1 \\rangle $2", options: "mA"},
    {trigger: "outer", replacement: "| ${0:\\psi} \\rangle \\langle ${0:\\psi} |", options: "mA"},
	{trigger: "ketbra", replacement: "| ${0:\\psi} \\rangle \\langle ${1:\\phi} |", options: "mA"},
	{trigger: "matel", replacement: "\\langle ${0:\\psi} | ${1:A} | ${2:\\psi} \\rangle $3", options: "mA"},
	{trigger: "expect", replacement: "\\langle ${0:A} \\rangle $1", options: "mA"},
	{trigger: "comm", replacement: "[${0:A}, ${1:B}]$2", options: "mA"},
	{trigger: "acomm", replacement: "\\{${0:A}, ${1:B}\\}$2", options: "mA"},
    {trigger: "dag", replacement: "^{\\dagger}", options: "mA"},
	{trigger: "herm", replacement: "^{\\dagger}", options: "mA"},
	{trigger: "hbar", replacement: "\\hbar", options: "mA"},
	{trigger: "pauli", replacement: "\\sigma^{$0}$1", options: "mA"},
	{trigger: "gam", replacement: "\\gamma^{$0}$1", options: "mA"},
	{trigger: "gam5", replacement: "\\gamma^{5}", options: "mA"},
	{trigger: "slash", replacement: "\\!\\!\\!/", options: "mA"},

    // ====================
    // QUANTUM FIELD THEORY
    // ====================
	{trigger: "lag", replacement: "\\mathcal{L}", options: "mA"},
	{trigger: "ham", replacement: "\\mathcal{H}", options: "mA"},
	{trigger: "act", replacement: "\\mathcal{S}", options: "mA"},
	{trigger: "pint", replacement: "\\int \\mathcal{D}${0:\\phi} \\, $1", options: "mA"},
	{trigger: "vev", replacement: "\\langle ${0:0} | ${1:\\phi} | ${0:0} \\rangle $2", options: "mA"},
	{trigger: "normal", replacement: ":\\! ${0:A} \\!:$1", options: "mA"},
	{trigger: "corr", replacement: "\\langle ${0:A} ${1:B} \\rangle $2", options: "mA"},
	{trigger: "ncorr", replacement: "\\langle ${0:A} ${1:B} \\cdots \\rangle $2", options: "mA"},
	{trigger: "Tprod", replacement: "\\mathcal{T}", options: "mA"},
	{trigger: "Feyn", replacement: "\\mathcal{F}", options: "mA"},

    // ====================
    // STATISTICAL MECHANICS
    // ====================
	{trigger: "part", replacement: "\\mathcal{Z}", options: "mA"},
	{trigger: "pf", replacement: "\\mathcal{Z}", options: "mA"},
	{trigger: "ens", replacement: "\\langle $0 \\rangle $1", options: "mA"},
	{trigger: "free", replacement: "\\mathcal{F}", options: "mA"},
	{trigger: "ent", replacement: "\\mathcal{S}", options: "mA"},
	{trigger: "gibbs", replacement: "e^{-\\beta ${0:H}}$1", options: "mA"},
	{trigger: "beta", replacement: "\\beta", options: "mA"},
	{trigger: "kbt", replacement: "k_{B}T", options: "mA"},
	{trigger: "kB", replacement: "k_{B}", options: "mA"},

    // ====================
    // PHYSICS CONSTANTS & UNITS
    // ====================
	{trigger: "msun", replacement: "M_{\\odot}", options: "mA"},
	{trigger: "hbar", replacement: "\\hbar", options: "mA"},
	{trigger: "planck", replacement: "\\ell_{\\mathrm{P}}", options: "mA"},

    // ====================
    // TRIGONOMETRY
    // ====================
    {trigger: /([^\\])(arcsin|sin|arccos|cos|arctan|tan|csc|sec|cot)/, replacement: "[[0]]\\[[1]]", options: "rmA"},
    {trigger: /\\(arcsin|sin|arccos|cos|arctan|tan|csc|sec|cot)([A-Za-gi-z])/, replacement: "\\[[0]] [[1]]", options: "rmA"},
    {trigger: /\\(sinh|cosh|tanh|coth)([A-Za-z])/, replacement: "\\[[0]] [[1]]", options: "rmA"},

    // ====================
    // COMMON MATHEMATICAL SYMBOLS
    // ====================
	{trigger: "ell", replacement: "\\ell", options: "mA"},
	{trigger: "hbar", replacement: "\\hbar", options: "mA"},
	{trigger: "imath", replacement: "\\imath", options: "mA"},
	{trigger: "jmath", replacement: "\\jmath", options: "mA"},
	{trigger: "wp", replacement: "\\wp", options: "mA"},
	{trigger: "Re", replacement: "\\Re", options: "mA"},
	{trigger: "Im", replacement: "\\Im", options: "mA"},
	{trigger: "eth", replacement: "\\eth", options: "mA"},
	{trigger: "mho", replacement: "\\mho", options: "mA"},
	{trigger: "natural", replacement: "\\natural", options: "mA"},
	{trigger: "sharp", replacement: "\\sharp", options: "mA"},
	{trigger: "flat", replacement: "\\flat", options: "mA"},
	{trigger: "clubsuit", replacement: "\\clubsuit", options: "mA"},
	{trigger: "diamondsuit", replacement: "\\diamondsuit", options: "mA"},
	{trigger: "heartsuit", replacement: "\\heartsuit", options: "mA"},
	{trigger: "spadesuit", replacement: "\\spadesuit", options: "mA"},
	{trigger: "checkmark", replacement: "\\checkmark", options: "mA"},
	{trigger: "smiley", replacement: "\\smiley", options: "mA"},
	{trigger: "frown", replacement: "\\frown", options: "mA"},

    // ====================
    // ENVIRONMENTS
    // ====================
	{trigger: "pmat", replacement: "\\begin{pmatrix}\n$0\n\\end{pmatrix}", options: "MA"},
	{trigger: "bmat", replacement: "\\begin{bmatrix}\n$0\n\\end{bmatrix}", options: "MA"},
	{trigger: "Bmat", replacement: "\\begin{Bmatrix}\n$0\n\\end{Bmatrix}", options: "MA"},
	{trigger: "vmat", replacement: "\\begin{vmatrix}\n$0\n\\end{vmatrix}", options: "MA"},
	{trigger: "Vmat", replacement: "\\begin{Vmatrix}\n$0\n\\end{Vmatrix}", options: "MA"},
	{trigger: "matrix", replacement: "\\begin{matrix}\n$0\n\\end{matrix}", options: "MA"},
	{trigger: "cases", replacement: "\\begin{cases}\n$0\n\\end{cases}", options: "mA"},
	{trigger: "align", replacement: "\\begin{align}\n$0\n\\end{align}", options: "mA"},
	{trigger: "array", replacement: "\\begin{array}\n$0\n\\end{array}", options: "mA"},
	{trigger: "split", replacement: "\\begin{split}\n$0\n\\end{split}", options: "mA"},
	{trigger: "gather", replacement: "\\begin{gather}\n$0\n\\end{gather}", options: "mA"},
	{trigger: "tikz", replacement: "\\begin{tikzpicture}\n$0\n\\end{tikzpicture}", options: "mA"},

	// Inline versions
	{trigger: "pmat", replacement: "\\begin{pmatrix}$0\\end{pmatrix}", options: "nA"},
	{trigger: "bmat", replacement: "\\begin{bmatrix}$0\\end{bmatrix}", options: "nA"},
	{trigger: "Bmat", replacement: "\\begin{Bmatrix}$0\\end{Bmatrix}", options: "nA"},
	{trigger: "vmat", replacement: "\\begin{vmatrix}$0\\end{vmatrix}", options: "nA"},
	{trigger: "Vmat", replacement: "\\begin{Vmatrix}$0\\end{Vmatrix}", options: "nA"},

    // ====================
    // BRACKETS
    // ====================
	{trigger: "avg", replacement: "\\langle $0 \\rangle $1", options: "mA"},
	{trigger: "angled", replacement: "\\langle $0 \\rangle $1", options: "mA"},
	{trigger: "norm", replacement: "\\lvert $0 \\rvert $1", options: "mA", priority: 1},
	{trigger: "Norm", replacement: "\\lVert $0 \\rVert $1", options: "mA", priority: 1},
	{trigger: "abs", replacement: "|$0|$1", options: "mA"},
	{trigger: "ceil", replacement: "\\lceil $0 \\rceil $1", options: "mA"},
	{trigger: "floor", replacement: "\\lfloor $0 \\rfloor $1", options: "mA"},
	{trigger: "(", replacement: "(${VISUAL})", options: "mA"},
	{trigger: "[", replacement: "[${VISUAL}]", options: "mA"},
	{trigger: "{", replacement: "{${VISUAL}}", options: "mA"},
	{trigger: "(", replacement: "($0)$1", options: "mA"},
	{trigger: "{", replacement: "{$0}$1", options: "mA"},
	{trigger: "[", replacement: "[$0]$1", options: "mA"},
	{trigger: "lr(", replacement: "\\left( $0 \\right) $1", options: "mA"},
	{trigger: "lr{", replacement: "\\left\\{ $0 \\right\\} $1", options: "mA"},
	{trigger: "lr[", replacement: "\\left[ $0 \\right] $1", options: "mA"},
	{trigger: "lr|", replacement: "\\left| $0 \\right| $1", options: "mA"},
	{trigger: "lra", replacement: "\\left\\langle $0 \\right\\rangle $1", options: "mA"},

    // ====================
    // VISUAL OPERATIONS
    // ====================
	{trigger: "U", replacement: "\\underbrace{ ${VISUAL} }_{ $0 }", options: "mA"},
	{trigger: "O", replacement: "\\overbrace{ ${VISUAL} }^{ $0 }", options: "mA"},
	{trigger: "B", replacement: "\\underset{ $0 }{ ${VISUAL} }", options: "mA"},
	{trigger: "C", replacement: "\\cancel{ ${VISUAL} }", options: "mA"},
	{trigger: "K", replacement: "\\cancelto{ $0 }{ ${VISUAL} }", options: "mA"},
	{trigger: "S", replacement: "\\sqrt{ ${VISUAL} }", options: "mA"},

    // ====================
    // CHEMISTRY
    // ====================
	{trigger: "pu", replacement: "\\pu{ $0 }", options: "mA"},
	{trigger: "cee", replacement: "\\ce{ $0 }", options: "mA"},
	{trigger: "he4", replacement: "{}^{4}_{2}He ", options: "mA"},
	{trigger: "he3", replacement: "{}^{3}_{2}He ", options: "mA"},
	{trigger: "isotope", replacement: "{}^{${0:A}}_{${1:Z}}${2:X}$3", options: "mA"},

    // ====================
    // SPECIAL FUNCTIONS
    // ====================
	{trigger: "tayl", replacement: "${0:f}(${1:x} + ${2:h}) = ${0:f}(${1:x}) + ${0:f}'(${1:x})${2:h} + ${0:f}''(${1:x}) \\frac{${2:h}^{2}}{2!} + \\dots$3", options: "mA"},
	{trigger: /iden(\d)/, replacement: (match) => {
		const n = match[1];
		let arr = [];
		for (let j = 0; j < n; j++) {
			arr[j] = [];
			for (let i = 0; i < n; i++) {
				arr[j][i] = (i === j) ? 1 : 0;
			}
		}
		let output = arr.map(el => el.join(" & ")).join(" \\\\\n");
		output = `\\begin{pmatrix}\n${output}\n\\end{pmatrix}`;
		return output;
	}, options: "mA"},

    // ====================
    // HANDLE SPACES AND BACKSLASHES
    // ====================
	{trigger: "([^\\\\])(${GREEK})", replacement: "[[0]]\\[[1]]", options: "rmA"},
	{trigger: "([^\\\\])(${SYMBOL})", replacement: "[[0]]\\[[1]]", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}|${MORE_SYMBOLS})([A-Za-z])", replacement: "\\[[0]] [[1]]", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) sr", replacement: "\\[[0]]^{2}", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) cb", replacement: "\\[[0]]^{3}", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) rd", replacement: "\\[[0]]^{$0}$1", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) uu", replacement: "\\[[0]]^{$0}$1", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) dd", replacement: "\\[[0]]_{$0}$1", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) hat", replacement: "\\hat{\\[[0]]}", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) dot", replacement: "\\dot{\\[[0]]}", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) bar", replacement: "\\bar{\\[[0]]}", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) vec", replacement: "\\vec{\\[[0]]}", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) tilde", replacement: "\\tilde{\\[[0]]}", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) und", replacement: "\\underline{\\[[0]]}", options: "rmA"}
]