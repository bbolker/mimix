Basic problem is that Mamba is old, suggestion is to update to Turing.jl (but that would take a complete overhaul). Instead I have forked Mamba and commented out the problematic version dependencies

The other approach would be to try to downgrade all package versions to get to a sufficiently old/compatible set.

* This could be done within a project (I think you can use different versions of packages on the same system in Julia)
* or build a Docker container with appropriately old versions of everything

Testing Mamba to make sure I haven't broken anything obvious, but way slow (maybe hanging?)

Then will try Mimix

using Pkg;
Pkg.add(url="https://github.com/bbolker/Mamba.jl.git")

or 

add https://github.com/bbolker/Mamba.jl.git

import Pkg; Pkg.add("ArgParse")
import Pkg; Pkg.add("CSV")
import Pkg; Pkg.add("DataFrames")

WARNING: Method definition (::Type{Distributions.Dirichlet{T, Ts, S} where S<:Real where Ts<:AbstractArray{T, 1} where T<:Real})(AbstractArray{T, 1}) where {T<:Real} in module Distributions at /home/bolker/.julia/packages/Distributions/psM3H/src/multivariate/dirichlet.jl:39 overwritten in module Mamba at /home/bolker/.julia/packages/Mamba/IEn4c/src/distributions/constructors.jl:17.
