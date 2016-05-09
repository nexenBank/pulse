# Pulse
##PulseProcessor

See https://docs.google.com/presentation/d/1IQ1UYyalwdcdMpbiiICll5CpRtQT6_ZukPHlnKFoaMQ/edit?usp=sharing for an overview of target architecture

###Key Items:
- Provide a scalable endpoint for fairly high speed telemetry
  - REST endpoint for simplicity behind a load balancer
  - Pass the results to a store via a KAFKA Layer
- Distribute load horizontally to scale
  - Use Hazelcast to share the data across several instances
  - Cache based on processing day (allow old days to be purged)
  - Use hazlecast instance Id to hash, preventing cascading updates from Esper engines
- Instances of processors aligned by 'System'
- use Esper to add rule processing engine
  - Republish backinto Hazelcast cache so REST Services can use it for dashboard demands
- Rest Service wraps up various GETS
  - Standard Heirarchy of Systems Components and Key Measures based on suplied values
  - Systems Components are related
  - Key Measures are embedded


