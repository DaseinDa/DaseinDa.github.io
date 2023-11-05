---
layout: default
title: misc
permalink: /misc/
subtitle: My Life
---

## More about me
* Hello, my name in Chinese is 金鑫, grown up at Chengdu, a culturally diverse, inclusive and beautiful city.
* I was sent to learn violin as a child, because I was shocked by piano's size and keyboard 88 number, and thought that the violin was more cute and lovely to suit me. The fact turns out that I was too young too simple :) a sad story, I am still strugling with pitch's accuracy after so many years.
* When at undergraduate, I was a member of the university's high-level orchestra. And also play bands a bit(I floated between different bands as a keyboard player, and did not stay at a stable one). 
* I often rent a digital piano in my student dormitory so I don't disturb others. But it has to be said that a mechanical piano can better express the layers and intensity control of the music.
<audio controls>
  <source src="/assets/audio/Youth+Dream+Place.mp3" type="audio/mp3">
</audio>

<figure>

  <audio
    src="/assets/audio/Youth+Dream+Place.mp3"

    title="Youth's DayDearm"
    {% if include.autoplay %}autoplay{% endif %}
    {% if include.controls %}controls{% endif %}
    {% if include.loop %}loop{% endif %}
    {% if include.muted %}muted{% endif %}
  />

  {%- if include.caption -%}<figcaption class="caption">{{ include.caption }}</figcaption>{%- endif %}

</figure>

<h3>芒种(Miscanthus)</h3>
<audio controls>
  <source src="/assets/audio/芒种.mp3" type="audio/mp3">
</audio>

{% include audio.html src="/assets/audio/芒种.mp3" %}

<video style="width= 50%; height=50%; object-fit: fill" controls="controls">
  <source src="/assets/video/MoonRiver.mp4" type="video/mp4">
</video>