<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns:sec="http://www.springframework.org/schema/security"
xmlns="http://www.springframework.org/schema/beans" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xmlns:jee="http://www.springframework.org/schema/jee" xmlns:p="http://www.springframework.org/schema/p" xmlns:aop="http://www.springframework.org/schema/aop" xmlns:context="http://www.springframework.org/schema/context"
xsi:schemaLocation="http://www.s //www.springframework.org/schema/beans
http://www.springframework.org/schema/security http://www.springframework.org/schema/context http://www.springframework.org/schema/aop
http://www.springframework.org/schema/tx
http://www.springframework.org/schema/jee’’> ‎<sec:http
entry-point-ref="casProcessingFilterEntryPoint"
access-decision-manager-ref="accessDecisionManager"
auto-config="true" use-expressions="true">
<sec:csrf disabled="true" />
<sec:intercept-url pattern="/accessDenied.*" />
<sec:intercept-url pattern="/pages/maintenance/AlternateCurrencySearch.jsf"
access="hasAuthority ('INT ALT CURRENCY.read')" />
<sec:intercept-url pattern="/pages/maintenance/CompanyNumber.jsf" access="hasAuthority('INT COMPANY NUMBER.read')" />
<sec: intercept-url
pattern="/pages/maintenance/FxRateSuspensionMaintenance.jsf" access="hasAuthority('INT FX RATE SUSPENSION.read pattern="/pages/maintenance/IntesCodeMaintenance.jsf" <sec: intercept-url pattern="
access="hasAuthority('INT <sec:intercept-url
pattern="/pages/maintenance/FXRateHistory.jsf" access="hasAuthority('INT FX RATES HISTORY.read')" /
< sec:intercept-url pattern="/**" access="hasRole('ROLE_USER')" />
< sec:custom-filter position="CAS_FILTER"
ref="casAuthenticationFilter" />
<sec:access-denied-handler ref="accessDeniedHandler" />
<sec:logout logout-url="/j_spring_cas_security_logout" success-handler-ref="dciLogoutSuccessHandler"
invalidate-session="true" />
</sec:http>
<bean id="access DeniedHandler"
class="com.dcisc.common.security.authentication.handler.CommonAccessDeniedHandler"> <property name="accessDeniedUrl" value="/interchange-web/accessDenied.xhtml" />
</bean>
<property name="auditManager" ref="auditManager" />
</beans>
