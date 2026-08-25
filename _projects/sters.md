---
title: STERS
subtitle: An Active-Toe-Coupled Spring–Tendon Energy Recirculation System for Bipedal Locomotion
description: STERS couples an active toe and the ankle through a shared spring-tendon pathway, enabling cross-joint energy storage, transfer, and release during multi-stage foot-ground contact.
short_label: Bio-inspired bipedal robotics
thumbnail: /assets/images/projects/sters/sters-cover.png
thumbnail_alt: STERS biological inspiration, spring-tendon mechanism, and bipedal robot platforms
hero: /assets/images/projects/sters/sters-cover.png
hero_alt: Biological tendon inspiration, the STERS ankle-toe mechanism, and two bipedal robot platforms
order: 1
selected: true
published: true
video: "#project-video"
tags:
  - Bio-inspired Robotics
  - Bipedal Locomotion
  - Elastic Actuation
  - Reinforcement Learning
---

<section class="project-section" id="overview">
  <header class="section-heading">
    <p class="section-kicker">01 · Biological inspiration</p>
    <h2>Overview</h2>
  </header>
  <div class="project-prose">
    <p>In mammalian hindlimbs, the Achilles tendon and plantar fascia form a continuous force-transmission pathway rather than acting as isolated elastic tissues. STERS translates that idea into a robotic mechanism: a spring-tendon path spans the ankle and an active toe, forming a multi-joint parallel elastic actuator.</p>
    <p>The ankle is the primary energy-input and load-regulation joint. The toe changes pathway geometry, manages contact transition, and contributes to late-stance energy release. This shared structure allows mechanical energy to move across joints while the controller preserves stable heel-to-toe walking.</p>
  </div>
  <figure class="research-figure figure-surface">
    <a class="figure-link" href="{{ '/assets/images/projects/sters/sters-overview.png' | relative_url }}" target="_blank" rel="noopener noreferrer" aria-label="Open the STERS overview figure at full size">
      <img src="{{ '/assets/images/projects/sters/sters-overview.png' | relative_url }}" alt="Biological inspiration, STERS mechanism, contact stages, and energy pathway" width="1972" height="692" loading="lazy">
    </a>
    <figcaption>From biological architecture to the active-toe-coupled spring-tendon mechanism and its stance-phase energy pathway. Select the figure to view it at full size.</figcaption>
  </figure>
</section>

<section class="project-section" id="energy-recirculation">
  <header class="section-heading">
    <p class="section-kicker">02 · Stance-phase mechanics</p>
    <h2>Energy Recirculation Across the Stance Phase</h2>
  </header>
  <div class="project-prose">
    <p>STERS interprets stance as four contact-related stages: heel strike, spring load, ankle lift, and push off. During heel strike and spring load, forward body motion dorsiflexes the ankle, lengthens the tendon path, and stores mechanical work as elastic energy.</p>
    <p>During ankle lift, the stored energy assists ankle extension and heel rise while tendon-induced toe torque supports contact. Push off coordinates the active toe and ankle to release the remaining energy. The dominant transfer remains on the ankle side, with the toe regulating the distal geometry and terminal contact.</p>
  </div>
  <figure class="research-figure research-figure--portrait figure-surface">
    <a class="figure-link" href="{{ '/assets/images/projects/sters/sters-energy-recirculation.png' | relative_url }}" target="_blank" rel="noopener noreferrer" aria-label="Open the stance-phase energy recirculation figure at full size">
      <img src="{{ '/assets/images/projects/sters/sters-energy-recirculation.png' | relative_url }}" alt="Heel strike, spring load, ankle lift, and push off energy recirculation stages" width="934" height="872" loading="lazy">
    </a>
  </figure>
</section>

<section class="project-section" id="dynamics">
  <header class="section-heading">
    <p class="section-kicker">03 · Mechanism model</p>
    <h2>Dynamics and Stiffness Optimization</h2>
  </header>
  <div class="project-prose">
    <p>Ankle and toe rotations jointly change the total tendon length. Tendon deformation, together with spring stiffness, determines tendon force; the routing geometry then maps that shared force to elastic torques at the ankle and toe through their effective moment arms.</p>
    <p>Stiffness is not selected empirically in isolation. An ankle-centered optimization models the stance leg as an inverted pendulum and balances the center-of-mass-induced gravitational torque against STERS elastic torque, minimizing the residual positive work required from the ankle motor during spring loading.</p>
  </div>
  <div class="figure-grid">
    <figure class="research-figure figure-surface">
      <a class="figure-link" href="{{ '/assets/images/projects/sters/sters-dynamics-model.png' | relative_url }}" target="_blank" rel="noopener noreferrer" aria-label="Open the STERS dynamics model at full size">
        <img src="{{ '/assets/images/projects/sters/sters-dynamics-model.png' | relative_url }}" alt="Tendon routing, joint angles, tendon length, force, moment arms, and joint torque mapping" width="772" height="538" loading="lazy">
      </a>
      <figcaption>Multi-input, multi-output spring-tendon force and torque model.</figcaption>
    </figure>
    <figure class="research-figure figure-surface">
      <a class="figure-link" href="{{ '/assets/images/projects/sters/sters-stiffness-optimization.png' | relative_url }}" target="_blank" rel="noopener noreferrer" aria-label="Open the stiffness optimization figure at full size">
        <img src="{{ '/assets/images/projects/sters/sters-stiffness-optimization.png' | relative_url }}" alt="Inverted-pendulum model, ankle torque map, motor work, and optimized spring stiffness" width="771" height="730" loading="lazy">
      </a>
      <figcaption>Ankle-centered stiffness optimization based on dynamics and motor work.</figcaption>
    </figure>
  </div>
</section>

<section class="project-section" id="contact-aware-locomotion">
  <header class="section-heading">
    <p class="section-kicker">04 · Foot-ground interaction</p>
    <h2>Contact-Aware Locomotion</h2>
  </header>
  <div class="project-prose">
    <p>STERS does not assume a single stance condition. Heel strike, spring load, ankle lift, and push off are represented through contact-related stages that describe how the segmented foot progresses from rear-foot contact to terminal toe support.</p>
    <p>This representation connects foot-contact logic to gait guidance and reward design. It gives the policy a consistent way to coordinate ankle and toe motion while interpreting when the elastic pathway should store or release energy.</p>
  </div>
  <figure class="research-figure research-figure--medium figure-surface">
    <a class="figure-link" href="{{ '/assets/images/projects/sters/sters-contact-transition.png' | relative_url }}" target="_blank" rel="noopener noreferrer" aria-label="Open the contact-transition figure at full size">
      <img src="{{ '/assets/images/projects/sters/sters-contact-transition.png' | relative_url }}" alt="Contact transitions and gait-consistency representation across stance" width="990" height="645" loading="lazy">
    </a>
  </figure>
</section>

<section class="project-section" id="reinforcement-learning">
  <header class="section-heading">
    <p class="section-kicker">05 · Learning and deployment</p>
    <h2>Reinforcement Learning and Control</h2>
  </header>
  <div class="project-prose">
    <p>Contact-stage gait guidance contributes step and gait-consistency rewards to a PPO policy. The policy produces joint-position actions inside a physics simulation, where the STERS model converts the current ankle and toe configuration into tendon-induced torques applied to the robot dynamics.</p>
    <p>Domain randomization includes spring stiffness and the initial ankle configuration, helping the learned behavior remain robust to mechanism variation. On hardware, the actor policy runs on the onboard Intel NUC, while low-level PD control and foot-contact logic translate policy actions to the real robot.</p>
  </div>
  <figure class="research-figure research-figure--dense figure-surface">
    <a class="figure-link" href="{{ '/assets/images/projects/sters/sters-rl-framework.png' | relative_url }}" target="_blank" rel="noopener noreferrer" aria-label="Open the reinforcement learning framework at full size">
      <img src="{{ '/assets/images/projects/sters/sters-rl-framework.png' | relative_url }}" alt="Gait guidance, reward, PPO, simulation, domain randomization, and STERS dynamics framework" width="1484" height="752" loading="lazy">
    </a>
    <figcaption>Physics-aware PPO training with contact-stage gait guidance and explicit STERS dynamics.</figcaption>
  </figure>

  <div class="supporting-media">
    <figure class="research-figure research-figure--medium figure-surface">
      <a class="figure-link" href="{{ '/assets/images/projects/sters/sters-control-framework.png' | relative_url }}" target="_blank" rel="noopener noreferrer" aria-label="Open the real-robot control framework at full size">
        <img src="{{ '/assets/images/projects/sters/sters-control-framework.png' | relative_url }}" alt="Simulation-to-real control framework with actor policy, onboard computer, PD controller, and robot" width="752" height="364" loading="lazy">
      </a>
      <figcaption>Supporting deployment architecture from training to onboard real-robot control.</figcaption>
    </figure>

    <div class="video-panel video-panel--portrait">
      <div class="media-heading">
        <p class="card-label">Simulation</p>
        <h3>Contact-stage walking in simulation</h3>
      </div>
      <video muted autoplay loop playsinline controls preload="metadata" poster="{{ '/assets/images/projects/sters/sters-cover.png' | relative_url }}" aria-label="STERS simulation walking video">
        <source src="{{ '/assets/videos/sters/sters-simulation-walking.mp4' | relative_url }}" type="video/mp4">
        Your browser does not support HTML video.
      </video>
    </div>
  </div>
</section>

<section class="project-section" id="model-validation">
  <header class="section-heading">
    <p class="section-kicker">06 · Physical model check</p>
    <h2>Experimental Model Validation</h2>
  </header>
  <div class="project-prose">
    <p>The spring-tendon model is checked against a physical loading and unloading experiment rather than treated only as a simulation assumption. A force sensor records the tendon response as the mechanism moves through the tested ankle range.</p>
    <p>The initial geometric estimate shows a clear mismatch with measurement. After calibration, the model-estimated response follows the measured loading and unloading behavior more closely, providing a physically grounded model for subsequent analysis and policy training.</p>
  </div>
  <figure class="research-figure research-figure--validation figure-surface">
    <a class="figure-link" href="{{ '/assets/images/projects/sters/sters-model-validation.png' | relative_url }}" target="_blank" rel="noopener noreferrer" aria-label="Open the physical model-validation figure at full size">
      <img src="{{ '/assets/images/projects/sters/sters-model-validation.png' | relative_url }}" alt="Physical tendon-force experiment and measured-versus-model-estimated loading and unloading response" width="2770" height="3497" loading="lazy">
    </a>
    <figcaption>Physical setup and comparison between sensor measurements and model estimates.</figcaption>
  </figure>
</section>

<section class="project-section" id="real-world-locomotion">
  <header class="section-heading">
    <p class="section-kicker">07 · Hardware evidence</p>
    <h2>Real-World Locomotion</h2>
  </header>
  <div class="project-prose">
    <p>Hardware trials demonstrate continuous outdoor walking on the BioLeg platform and provide frame-by-frame evidence of the segmented foot moving through heel-to-toe contact. The sequences below are presented without assigning unverified configuration labels to the individual image rows.</p>
  </div>
  <div class="figure-stack">
    <figure class="research-figure figure-surface">
      <a class="figure-link" href="{{ '/assets/images/projects/sters/sters-real-gait.png' | relative_url }}" target="_blank" rel="noopener noreferrer" aria-label="Open the real-robot gait sequence at full size">
        <img src="{{ '/assets/images/projects/sters/sters-real-gait.png' | relative_url }}" alt="Outdoor real-robot gait sequence" width="1147" height="517" loading="lazy">
      </a>
    </figure>
    <figure class="research-figure research-figure--medium figure-surface">
      <a class="figure-link" href="{{ '/assets/images/projects/sters/sters-gait-comparison.png' | relative_url }}" target="_blank" rel="noopener noreferrer" aria-label="Open the real gait comparison at full size">
        <img src="{{ '/assets/images/projects/sters/sters-gait-comparison.png' | relative_url }}" alt="Three observed real-robot foot-contact sequences" width="758" height="409" loading="lazy">
      </a>
    </figure>
  </div>

  <div class="video-grid">
    <div class="video-panel video-panel--portrait">
      <div class="media-heading"><p class="card-label">Real robot · view 01</p></div>
      <video muted autoplay loop playsinline controls preload="metadata" poster="{{ '/assets/images/projects/sters/sters-cover.png' | relative_url }}" aria-label="BioLeg outdoor walking video, view one">
        <source src="{{ '/assets/videos/sters/sters-real-walking-1.mp4' | relative_url }}" type="video/mp4">
        Your browser does not support HTML video.
      </video>
    </div>
    <div class="video-panel video-panel--portrait">
      <div class="media-heading"><p class="card-label">Real robot · view 02</p></div>
      <video muted autoplay loop playsinline controls preload="metadata" poster="{{ '/assets/images/projects/sters/sters-cover.png' | relative_url }}" aria-label="BioLeg outdoor walking video, view two">
        <source src="{{ '/assets/videos/sters/sters-real-walking-2.mp4' | relative_url }}" type="video/mp4">
        Your browser does not support HTML video.
      </video>
    </div>
  </div>
</section>

<section class="project-section" id="disturbance-recovery">
  <header class="section-heading">
    <p class="section-kicker">08 · Robustness</p>
    <h2>Disturbance Recovery</h2>
  </header>
  <div class="project-prose">
    <p>A magnet, detacher, free-falling mass, and timed rope release create controlled disturbances for repeatable recovery tests. The experiment evaluates static stability and separates the contribution of the active toe from the additional effect of the spring-tendon mechanism.</p>
    <p>Across both BioLeg and Roboto Origin, the active toe is the dominant structural factor in recovery. The complete STERS configuration generally provides a further, smaller improvement.</p>
  </div>
  <div class="supporting-media supporting-media--impact">
    <figure class="research-figure figure-surface">
      <a class="figure-link" href="{{ '/assets/images/projects/sters/sters-impact-setup.png' | relative_url }}" target="_blank" rel="noopener noreferrer" aria-label="Open the disturbance experiment setup at full size">
        <img src="{{ '/assets/images/projects/sters/sters-impact-setup.png' | relative_url }}" alt="Controlled disturbance setup with magnet, detacher, falling mass, and rope release" width="1148" height="641" loading="lazy">
      </a>
    </figure>
    <div class="video-panel">
      <div class="media-heading"><p class="card-label">Impact recovery demo</p></div>
      <video muted autoplay loop playsinline controls preload="metadata" poster="{{ '/assets/images/projects/sters/sters-impact-setup.png' | relative_url }}" aria-label="Controlled impact recovery experiment video">
        <source src="{{ '/assets/videos/sters/sters-impact-demo.mp4' | relative_url }}" type="video/mp4">
        Your browser does not support HTML video.
      </video>
    </div>
  </div>
  <figure class="research-figure research-figure--dense research-figure--impact figure-surface">
    <a class="figure-link" href="{{ '/assets/images/projects/sters/sters-impact-results.png' | relative_url }}" target="_blank" rel="noopener noreferrer" aria-label="Open the complete impact-recovery results at full size">
      <img src="{{ '/assets/images/projects/sters/sters-impact-results.png' | relative_url }}" alt="Impact-recovery result heatmaps across robot configurations and disturbance conditions" width="2675" height="2903" loading="lazy">
    </a>
    <figcaption>Recovery time and success across disturbance conditions. Select the figure to inspect the dense result map at full size.</figcaption>
  </figure>
</section>

<section class="project-section" id="walking-performance">
  <header class="section-heading">
    <p class="section-kicker">09 · Quantitative evaluation</p>
    <h2>Walking Performance and Energy Efficiency</h2>
  </header>
  <div class="project-prose">
    <p>The hardware ablation compares three configurations on each platform. Group 1 uses the original single-segment planar foot and baseline training strategy. Group 2 adds an active toe with gait guidance. Group 3 adds the complete STERS spring-tendon mechanism and incorporates its dynamics into training.</p>
  </div>

  <dl class="metric-grid" aria-label="Key STERS results">
    <div>
      <dt>44.29%</dt>
      <dd>Lower leg energy consumption on BioLeg versus Group 1</dd>
    </div>
    <div>
      <dt>36.25%</dt>
      <dd>Lower leg energy consumption on Roboto Origin versus Group 1</dd>
    </div>
    <div>
      <dt>≈75%</dt>
      <dd>Lower peak ankle driving torque on BioLeg versus active-toe Group 2</dd>
    </div>
  </dl>

  <div class="project-prose">
    <p>Across the 7 m walking trials, complete STERS produced the lowest energy consumption on both platforms and the smallest terminal lateral deviation. The ankle-torque result indicates that the coupled elastic pathway supports part of the stance load and reduces the actuator's instantaneous demand.</p>
  </div>
  <figure class="research-figure research-figure--dense figure-surface">
    <a class="figure-link" href="{{ '/assets/images/projects/sters/sters-walking-results.png' | relative_url }}" target="_blank" rel="noopener noreferrer" aria-label="Open the complete walking and energy results at full size">
      <img src="{{ '/assets/images/projects/sters/sters-walking-results.png' | relative_url }}" alt="Seven-meter trajectories, energy use, ankle torque, and toe behavior for three ablation groups" width="1459" height="501" loading="lazy">
    </a>
    <figcaption>Walking trajectory, energy consumption, ankle torque, and toe behavior across the three ablation groups.</figcaption>
  </figure>
</section>

<section class="project-section" id="project-video">
  <header class="section-heading">
    <p class="section-kicker">10 · Video summary</p>
    <h2>Project Overview Video</h2>
  </header>
  <div class="long-video">
    <video controls preload="metadata" poster="{{ '/assets/images/projects/sters/sters-cover.png' | relative_url }}" aria-label="STERS project overview video">
      <source src="{{ '/assets/videos/sters/sters-project-overview.mp4' | relative_url }}" type="video/mp4">
      Your browser does not support HTML video.
    </video>
  </div>

  <details class="supplementary-video">
    <summary>Supplementary Demo</summary>
    <p>Additional mechanism, contact-stage, and ablation footage.</p>
    <video controls preload="none" poster="{{ '/assets/images/projects/sters/sters-overview.png' | relative_url }}" aria-label="STERS supplementary demonstration video">
      <source src="{{ '/assets/videos/sters/sters-supplementary-demo.mp4' | relative_url }}" type="video/mp4">
      Your browser does not support HTML video.
    </video>
  </details>
</section>

<section class="project-section" id="publication">
  <header class="section-heading">
    <p class="section-kicker">11 · Manuscript</p>
    <h2>Publication / BibTeX</h2>
  </header>
  <div class="publication-detail">
    <p class="publication-status">Under review at <em>IEEE/ASME Transactions on Mechatronics</em>.</p>
    <h3>An Active-Toe-Coupled Spring–Tendon Energy Recirculation System for Bipedal Locomotion</h3>
    <p>Wenyu Li, Zhiyuan Xu, Yuelong Zhang, Jiaxing Li, Jingang Yi, and Tao Liu</p>
    <p class="note">A clean public manuscript link will be added when an appropriate version is available.</p>
  </div>
  <pre class="bibtex"><code>@unpublished{li_sters,
  title  = {An Active-Toe-Coupled Spring--Tendon Energy Recirculation System for Bipedal Locomotion},
  author = {Li, Wenyu and Xu, Zhiyuan and Zhang, Yuelong and Li, Jiaxing and Yi, Jingang and Liu, Tao},
  note   = {Under review at IEEE/ASME Transactions on Mechatronics}
}</code></pre>
</section>
