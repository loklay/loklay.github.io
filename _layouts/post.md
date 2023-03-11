{% include header.html %}
<div class="section-container p-2 p-xl-4">
    <div class="row">
        <div class="col-md-8 ps-4 ps-lg-3">
            <div class="row bg-white shadow-sm">
                <div class="col-md-4 p-3">
                    <img class="w-100" src="{{page.thumbnail}}" alt="">
                </div>
                <div class="col-md-8 p-2">
                    <h4 class="fw-semi fs-4 mb-3">{{page.title}}</h4>
                    <a href="{{page.apk}}" download>
                        <button class="btn btn-primary w-45 fw-semi fs-8 py-2 me-3"> ཨན་ཌོ་ནང་དུ་ཕབ་ལེན།</button>
                    </a>
                    <div class="row pt-4">
                        <div class="col-md-4 col-6 text-center">
                            <b>{{page.rating}} <i class="bi bi-star-fill"></i></b>
                            <p>11.6k Reviews</p>
                        </div>
                            <div class="col-md-4 col-6 text-center">
                            <b>{{page.downloads}}</b>
                            <p>Downloads</p>
                        </div>
                    </div>
                    
                    <div class="auth pt-4">
                        <h6 class="text-primary fw-semi mb-0">GreatFire</h6>
                        <p class="fs-8">contains Ads</p>
                    </div>
                </div>
            </div>
            <div class="about row p-2 py-3 bg-white mt-4 shadow-sm">
                <h4 class="fw-semi fs-5">About this Application</h4>
                <p class="fs-8 text-justify">
                {{content}}

                </p>
            </div>
    </div>
    <div class="col-md-4">
        <h4 class="fs-6 fw-bolder my-3 mt-2 mb-3">Related Apps</h4>
             {% assign maxRelated = 5 %}
            {% assign minCommonTags =  1 %}
            {% assign maxRelatedCounter = 0 %}
            {% for post in site.posts %}

                {% assign sameTagCount = 0 %}
            
                {% for tag in post.tags %}
                    {% if post.url != page.url %}
                        {% if page.tags contains tag %}
                            {% assign sameTagCount = sameTagCount | plus: 1 %}
                        {% endif %}
                    {% endif %}
                {% endfor %}
            
                {% if sameTagCount >= minCommonTags %}
                    <div class="col-md-12 mb-3">
                        <div class="app-cover p-2 shadow-md bg-white">
                        <a href="single.html">
                            <div class="row">
                                    <div class="img-cover pe-0 col-3"> <img class="rounded" src="{{post.thumbnail}}" alt=""></div>
                                    <div class="det mt-2 col-9">
                                        <h5 class="mb-0 fs-6">{{post.title}}</h5>
                                        <span class="fs-8">{{post.category}}</span>
                                        <ul class="row">
                                            <li class="col-8 ratfac">
                                                <b>{{post.rating}} <i class="bi bi-star-fill"></i></b>
                                            </li>
                                            <li class="col-4"><span class="text-success float-end">Free</span></li>
                                        </ul>
                                    </div>
                            </div>
                        </a>
                    </div>
                </div>
                        {% assign maxRelatedCounter = maxRelatedCounter | plus: 1 %}
                        {% if maxRelatedCounter >= maxRelated %}
                            {% break %}
                        {% endif %}
                    {% endif %}
                {% endfor %}
                <!-- Adds related posts to the end of an article -->

    </div>

</div>