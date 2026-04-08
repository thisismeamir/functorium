---
sticker: lucide//atom
---
- [ ] Need refinement, copied from wikipedia.
# Sober space

In [mathematics](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Mathematics "Mathematics"), a **sober space** is a [topological space](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Topological_space "Topological space") _X_ such that every (nonempty) [irreducible](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Irreducible_space "Irreducible space") [closed subset](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Closed_subset "Closed subset") of _X_ is the [closure](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Closure_\(topology\) "Closure (topology)") of exactly one point of _X_: that is, every nonempty irreducible closed subset has a unique [generic point](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Generic_point "Generic point").

## Definitions

Sober spaces have a variety of [cryptomorphic](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Cryptomorphic "Cryptomorphic") definitions, which are documented in this section.[[1]](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Sober_space#cite_note-sheavesgeometrylogic-1)[[2]](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Sober_space#cite_note-nets-2) In each case below, replacing "unique" with "at most one" gives an equivalent formulation of the [T0 axiom](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Kolmogorov_space "Kolmogorov space"). Replacing it with "at least one" is equivalent to the property that the T0 [quotient](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Quotient_space_\(topology\) "Quotient space (topology)") of the space is sober, which is sometimes referred to as having "enough points" in the literature.

### With irreducible closed sets

A closed set is [irreducible](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Hyperconnected_space "Hyperconnected space") if it cannot be written as the union of two proper closed subsets. A space is **sober** if every nonempty irreducible closed subset is the closure of a unique point.

### In terms of morphisms of [frames and locales](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Complete_Heyting_algebra "Complete Heyting algebra")

A topological space _X_ is sober if every map from its [partially ordered set](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Partially_ordered_set "Partially ordered set") of open subsets to {0, 1} that preserves all [joins](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Join_\(order_theory\) "Join (order theory)") and all finite meets is the inverse image of a unique [continuous function](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Continuous_function "Continuous function") from the one-point space to _X_.

This may be viewed as a correspondence between the notion of a point in a locale and a point in a topological space, which is the motivating definition.

### Using completely prime filters

A [filter](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Filters_in_topology "Filters in topology") _F_ of open sets is said to be _completely prime_ if for any family Oi![{\displaystyle O_{i}}](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/_assets_/eb734a37dd21ce173a46342d1cc64c92/907f89d54862168ae54a66e6835115df7587954f.svg) of open sets such that ⋃iOi∈F![{\displaystyle \bigcup _{i}O_{i}\in F}](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/_assets_/eb734a37dd21ce173a46342d1cc64c92/a1dd82001376a3e4e0d06dc8202bddef8077dc07.svg), we have that Oi∈F![{\displaystyle O_{i}\in F}](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/_assets_/eb734a37dd21ce173a46342d1cc64c92/17c9f85b6cc96c16b0bd94b43329c1a46d16e61e.svg) for some _i_. A space _X_ is sober if each completely prime filter is the [neighbourhood filter](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Neighbourhood_filter "Neighbourhood filter") of a unique point in _X_.

### In terms of nets

A [net](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Net_\(mathematics\) "Net (mathematics)") x∙![{\displaystyle x_{\bullet }}](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/_assets_/eb734a37dd21ce173a46342d1cc64c92/61fc088fd942f558f51cd6ff44fdc6498e024ae7.svg) is _self-convergent_ if it converges to every point xi![{\displaystyle x_{i}}](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/_assets_/eb734a37dd21ce173a46342d1cc64c92/e87000dd6142b81d041896a30fe58f0c3acb2158.svg) in x∙![{\displaystyle x_{\bullet }}](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/_assets_/eb734a37dd21ce173a46342d1cc64c92/61fc088fd942f558f51cd6ff44fdc6498e024ae7.svg), or equivalently if its eventuality filter is completely prime. A net x∙![{\displaystyle x_{\bullet }}](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/_assets_/eb734a37dd21ce173a46342d1cc64c92/61fc088fd942f558f51cd6ff44fdc6498e024ae7.svg) that converges to x![{\displaystyle x}](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/_assets_/eb734a37dd21ce173a46342d1cc64c92/87f9e315fd7e2ba406057a97300593c4802b53e4.svg) _converges strongly_ if it can only converge to points in the closure of x![{\displaystyle x}](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/_assets_/eb734a37dd21ce173a46342d1cc64c92/87f9e315fd7e2ba406057a97300593c4802b53e4.svg). A space is sober if every self-convergent net x∙![{\displaystyle x_{\bullet }}](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/_assets_/eb734a37dd21ce173a46342d1cc64c92/61fc088fd942f558f51cd6ff44fdc6498e024ae7.svg) converges strongly to a unique point x![{\displaystyle x}](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/_assets_/eb734a37dd21ce173a46342d1cc64c92/87f9e315fd7e2ba406057a97300593c4802b53e4.svg).[[2]](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Sober_space#cite_note-nets-2)

In particular, a space is T1 and sober precisely if every self-convergent net is constant.

### As a property of sheaves on the space

A space _X_ is sober if every [functor](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Functor "Functor") from the category of [sheaves](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Sheaf_\(mathematics\) "Sheaf (mathematics)") _Sh_(_X_) to _Set_ that preserves all [finite limits](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Limit_\(category_theory\) "Limit (category theory)") and all [small colimits](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Small_colimit "Small colimit") must be the stalk functor of a unique point _x_.

## Properties and examples

Any [Hausdorff](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/T2_space "T2 space") (T2) space is sober (the only irreducible subsets being singletons), and all sober spaces are [Kolmogorov](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/T0_space "T0 space") (T0), and both implications are strict.[[3]](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Sober_space#cite_note-egt-3)

Sobriety is not [comparable](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Comparability "Comparability") to the [T1](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/T1_space "T1 space") condition:

- an example of a T1 space that is not sober is an infinite set with the [cofinite topology](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Cofinite_topology "Cofinite topology"), the whole space being an irreducible closed subset with no generic point;
- an example of a sober space that is not T1 is the [Sierpinski space](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Sierpinski_space "Sierpinski space").

Moreover, T2 is strictly stronger than T1 _and_ sober, i.e., while every T2 space is at once T1 and sober, there exist spaces that are simultaneously T1 and sober, but not T2. One such example is the following: let _X_ be the set of real numbers, with a new point _p_ adjoined; the open sets being all real open sets, and all cofinite sets containing _p_.

Sobriety of _X_ is precisely a condition that forces the [lattice of open subsets](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Lattice_\(order\) "Lattice (order)") of _X_ to determine _X_ [up to](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Up_to "Up to") [homeomorphism](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Homeomorphism "Homeomorphism"), which is relevant to [pointless topology](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Pointless_topology "Pointless topology").

Sobriety makes the specialization preorder a [directed complete partial order](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Directed_complete_partial_order "Directed complete partial order").

Every [continuous directed complete poset](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Domain_theory "Domain theory") equipped with the [Scott topology](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Scott_continuity "Scott continuity") is sober.

Finite T0 spaces are sober.[[4]](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Sober_space#cite_note-4)

The [prime spectrum](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Prime_spectrum "Prime spectrum") Spec(_R_) of a [commutative ring](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Commutative_ring "Commutative ring") _R_ with the [Zariski topology](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Zariski_topology "Zariski topology") is a [compact](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Compact_space "Compact space") sober space.[[3]](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Sober_space#cite_note-egt-3) In fact, every [spectral space](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Spectral_space "Spectral space") (i.e. a compact sober space for which the collection of compact open subsets is closed under finite intersections and forms a base for the topology) is homeomorphic to Spec(_R_) for some commutative ring _R_. This is a theorem of Melvin Hochster.[[5]](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Sober_space#cite_note-Hoch-5) More generally, the underlying topological space of any [scheme](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Scheme_\(mathematics\) "Scheme (mathematics)") is a sober space.

The subset of Spec(_R_) consisting only of the [maximal ideals](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Maximal_ideal "Maximal ideal"), where _R_ is a commutative ring, is not sober in general.